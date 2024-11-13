platform :ios, '13.0'

source 'https://cdn.cocoapods.org/'
source 'git@github.com:gonativeio/gonative-specs.git'  # Make sure Bitrise has access

# Ensure the plugins file exists or remove this if not using any plugins
require_relative './plugins.rb'  

target 'default_app_target' do
  use_frameworks!

  # Pods for GonativeIO
  pod 'GoNativeCore'
  pod 'MedianIcons'
  pod 'SSZipArchive'
  
  use_plugins!  # Ensure plugins.rb exists, or remove this if not using plugins

  target 'MedianIOSTests' do
    inherit! :search_paths
    # Pods for testing
  end
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings.delete 'IPHONEOS_DEPLOYMENT_TARGET'
      config.build_settings['BUILD_LIBRARY_FOR_DISTRIBUTION'] = 'YES'
      config.build_settings['CODE_SIGNING_ALLOWED'] = 'NO'
    end
  end
end

target 'OneSignalNotificationServiceExtension' do
  use_frameworks!
  pod 'OneSignal', '~> 3.12'
end
