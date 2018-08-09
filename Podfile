platform :ios, '10.0'
inhibit_all_warnings!
source 'https://github.com/CocoaPods/Specs.git'

target 'Hyperloot-iOS' do
  use_frameworks!

  pod 'BigInt', '~> 3.0'
  pod 'JSONRPCKit', :git=> 'https://github.com/bricklife/JSONRPCKit.git'
  pod 'APIKit'
  pod 'KeychainSwift'
  pod 'PromiseKit', '~> 6.0'
  pod 'SwiftLint'
  pod 'Moya', '~> 10.0.1'
  pod 'RealmSwift'
  pod 'CryptoSwift', '~> 0.10.0'
  pod 'TrustCore', '~> 0.0.7'
  pod 'TrustKeystore', :git=>'https://github.com/TrustWallet/trust-keystore', :commit=>'b338faf76d62efa570bd03088ebceac4e10314da'
  pod 'SAMKeychain'
  pod 'TrustWeb3Provider', :git=>'https://github.com/TrustWallet/trust-web3-provider', :commit=>'f4e0ebb1b8fa4812637babe85ef975d116543dfd'
  pod 'TrustWalletSDK', '0.0.1'

end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    if ['JSONRPCKit'].include? target.name
      target.build_configurations.each do |config|
        config.build_settings['SWIFT_VERSION'] = '3.0'
      end
    end
    if ['TrustKeystore'].include? target.name
      target.build_configurations.each do |config|
        config.build_settings['SWIFT_OPTIMIZATION_LEVEL'] = '-Owholemodule'
      end
    end
    if target.name != 'Realm'
        target.build_configurations.each do |config|
            config.build_settings['MACH_O_TYPE'] = 'staticlib'
        end
    end
  end
end