---
title: Určení vlastního šifrovacího algoritmu
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 673d177a665e265d77f0221e0a00f4b814c8795c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186479"
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Určení vlastního šifrovacího algoritmu
WCF umožňuje zadat vlastní kryptografický algoritmus, který se má použít při šifrování dat nebo výpočtu digitálních podpisů. To se provádí následujícími kroky:  
  
1. Odvodit třídu z<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2. Registrace algoritmu  
  
3. Nakonfigurujte <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>vazbu s -derived třídy.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>Odvodit třídu z SecurityAlgorithmSuite  
 Jedná <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> se o abstraktní základní třídu, která umožňuje určit algoritmus, který se má použít při provádění různých operací souvisejících se zabezpečením. Například výpočet hash pro digitální podpis nebo šifrování zprávy. Následující kód ukazuje, jak odvodit třídu z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a>Registrace vlastního algoritmu  
 Registrace může být provedena v konfiguračním souboru nebo v imperativním kódu. Registrace vlastního algoritmu se provádí vytvořením mapování mezi třídou, která implementuje poskytovatele kryptografických služeb a alias. Alias je pak mapován na identifikátor URI, který se používá při zadávání algoritmu ve vazbě služby WCF. Následující fragment konfigurace ukazuje, jak zaregistrovat vlastní algoritmus v konfiguraci:  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 Oddíl pod elementem <`cryptoClasses`> vytvoří mapování mezi sha256CryptoServiceProvider a alias "SHA256CSP". Element `nameEntry` <> vytvoří mapování mezi aliasem SHA256CSP `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`a zadanou adresou URL .  
  
 Chcete-li zaregistrovat vlastní <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> algoritmus v kódu použijte metodu. Tato metoda vytvoří obě mapování. Následující příklad ukazuje, jak volat tuto metodu:  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Konfigurace vazby  
 Vazbu nakonfigurujete zadáním třídy custom-derived <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>v nastavení vazby, jak je znázorněno v následujícím fragmentu kódu:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Úplný příklad kódu naleznete v [cryptografické agility v wcf zabezpečení](../samples/cryptographic-agility-in-wcf-security.md) vzorku.  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení služeb a klientů](../feature-details/securing-services-and-clients.md)
- [Zabezpečení služeb](../securing-services.md)
- [Přehled zabezpečení](../feature-details/security-overview.md)
- [Koncepce zabezpečení](../feature-details/security-concepts.md)
