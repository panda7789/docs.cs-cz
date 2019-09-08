---
title: Určení vlastního šifrovacího algoritmu
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: cf4b3da82087a6daade9d6b939f3e1aac628cb01
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796887"
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Určení vlastního šifrovacího algoritmu
WCF umožňuje zadat vlastní šifrovací algoritmus, který se použije při šifrování dat nebo výpočetních digitálních podpisů. To se provádí pomocí následujících kroků:  
  
1. Odvodit třídu z<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2. Registrovat algoritmus  
  
3. Nakonfigurujte vazbu s <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>třídou odvozenou.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>Odvození třídy z SecurityAlgorithmSuite  
 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Je abstraktní základní třída, která umožňuje určit algoritmus, který se má použít při provádění různých operací souvisejících se zabezpečením. Například výpočet hash pro digitální podpis nebo šifrování zprávy. Následující kód ukazuje, jak odvodit třídu z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:  
  
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
 Registraci je možné provést v konfiguračním souboru nebo v imperativně kódu. Registrace vlastního algoritmu se provádí vytvořením mapování mezi třídou, která implementuje poskytovatele kryptografických služeb a aliasu. Alias se pak namapuje na identifikátor URI, který se používá při zadávání algoritmu ve vazbě služby WCF. Následující fragment kódu ukazuje, jak zaregistrovat vlastní algoritmus v konfiguraci:  
  
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
  
 V části pod prvkem <`cryptoClasses`> se vytvoří mapování mezi SHA256CryptoServiceProvider a aliasem "SHA256CSP". Prvek <`nameEntry`> vytvoří mapování mezi alias "SHA256CSP" a zadanou adresou URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).  
  
 K registraci vlastního algoritmu v kódu použijte <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> metodu. Tato metoda vytvoří obě mapování. Následující příklad ukazuje, jak zavolat tuto metodu:  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Konfigurace vazby  
 Vazbu nakonfigurujete zadáním vlastní <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>odvozené třídy v nastavení vazby, jak je znázorněno v následujícím fragmentu kódu:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Úplný příklad kódu naleznete [v tématu kryptografická flexibilita v ukázce zabezpečení služby WCF](../samples/cryptographic-agility-in-wcf-security.md) .  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení služeb a klientů](../feature-details/securing-services-and-clients.md)
- [Zabezpečení služeb](../securing-services.md)
- [Přehled zabezpečení](../feature-details/security-overview.md)
- [Koncepty zabezpečení](../feature-details/security-concepts.md)
