# Permission-Xiaomi...
//Activity
@SuppressLint("BatteryLife")
    @RequiresApi(Build.VERSION_CODES.M)
    fun Context.requestIgnoreBatteryOptimizationPermission() {
        val intent = Intent()
        val packageName: String = this.packageName
        val pm: PowerManager = getSystemService(Context.POWER_SERVICE) as PowerManager
        if (!pm.isIgnoringBatteryOptimizations(packageName)) {
            intent.action = Settings.ACTION_REQUEST_IGNORE_BATTERY_OPTIMIZATIONS
            intent.data = Uri.parse("package:$packageName")
            startActivity(intent)
        }
    }
    
    //Fragment
    @SuppressLint("BatteryLife")
    @RequiresApi(Build.VERSION_CODES.M)
    private fun requestIgnoreBatteryOptimizationPermission(activity: Activity) {
        val intent = Intent()
        val packageName: String = activity.packageName
        val pm: PowerManager = activity.getSystemService(Context.POWER_SERVICE) as PowerManager
        if (!pm.isIgnoringBatteryOptimizations(packageName)) {
            intent.action = Settings.ACTION_REQUEST_IGNORE_BATTERY_OPTIMIZATIONS
            intent.data = Uri.parse("package:$packageName")
            activity.startActivity(intent)
        } else { //thêm
            //sharedPreferences.setPermissionBattery(true)
            intent.action = Settings.ACTION_IGNORE_BATTERY_OPTIMIZATION_SETTINGS
        }
    }
