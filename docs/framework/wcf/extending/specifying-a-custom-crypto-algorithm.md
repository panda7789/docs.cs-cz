---
title: Určení vlastního šifrovacího algoritmu
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: b365c3c8e74adcad03246a227d6593c49f8b3993
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342827"
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Určení vlastního šifrovacího algoritmu
WCF umožňuje určení vlastního šifrovacího algoritmu, který chcete použít, pokud k šifrování dat nebo výpočetní digitální podpisy. Uděláte to pomocí následujících kroků:  
  
1. Odvodit třídu z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2. Zaregistrujte algoritmus  
  
3. Konfigurace vazby s <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-odvozené třídy.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>Odvodit třídu z SecurityAlgorithmSuite  
 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Je abstraktní základní třída, která vám umožní určit algoritmus pro použití při provádění zabezpečení různých operací souvisejících s. Například výpočtu hodnoty hash pro digitální podpis nebo šifrování zprávy. Následující kód ukazuje, jak odvodit třídu z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:  
  
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
 Registrace může provést, v konfiguračním souboru nebo imperativního kódu. Registrace vlastního algoritmu se provádí tak, že vytvoříte mapování mezi třídy implementující zprostředkovatele kryptografických služeb a alias. Alias se pak namapuje na identifikátor URI, který se používá při určování algoritmus ve vazbě služby WCF. Následující konfigurace fragment kódu ukazuje, jak zaregistrovat vlastní algoritmus v konfiguraci:  
  
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
  
 Části <`cryptoClasses`> element vytvoří mapování mezi SHA256CryptoServiceProvider a alias "SHA256CSP". <`nameEntry`> Element vytvoří mapování mezi "SHA256CSP" alias a zadaná adresa URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).  
  
 K registraci vlastního algoritmu kód používá <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> metody. Tato metoda vytvoří oba mapování. Následující příklad ukazuje, jak volat tuto metodu:  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Konfiguraci vazby  
 Konfiguraci vazby tak, že zadáte vlastní <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-odvozené třídy v nastavení vazby, jak je znázorněno v následujícím fragmentu kódu:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Kompletní příklad, najdete v článku [kryptografická flexibilita v zabezpečení WCF](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) vzorku.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Zabezpečení služeb](../../../../docs/framework/wcf/securing-services.md)
- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)
