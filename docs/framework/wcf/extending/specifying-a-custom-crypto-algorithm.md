---
title: "Určení vlastního šifrovacího algoritmu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 965f121faa851722e6e2e7f92e805252f7e927c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Určení vlastního šifrovacího algoritmu
WCF umožňuje zadat vlastního šifrovacího algoritmu, který má použít při šifrování dat nebo výpočetní digitální podpisy. Uděláte to pomocí následujících kroků:  
  
1.  Odvození třídy z<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2.  Zaregistrovat algoritmus  
  
3.  Konfiguraci vazby s <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-odvozené třídy.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>Odvození třídy z SecurityAlgorithmSuite  
 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Je abstraktní základní třída, která vám umožní určit, že algoritmus použije při provádění různých zabezpečení operací souvisejících s. Například computing hodnotu hash pro digitální podpis nebo šifrování zprávy. Následující kód ukazuje, jak na odvození třídy z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:  
  
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
  
## <a name="register-the-custom-algorithm"></a>Zaregistrovat vlastní algoritmus  
 Registrace lze provést v konfiguračním souboru nebo v imperativní kódu. Registrace vlastní algoritmus se provádí tak, že vytvoříte mapování mezi třídu, která implementuje zprostředkovatele kryptografických služeb a alias. Alias je poté mapován na identifikátor URI, který se používá při zadávání algoritmus do vazby služby WCF. Následující fragment kódu konfigurace ukazuje, jak se zaregistrovat vlastní algoritmus v konfiguraci:  
  
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
  
 V části v rámci <`cryptoClasses`> element vytvoří mapování mezi SHA256CryptoServiceProvider a alias "SHA256CSP". <`nameEntry`> Element vytvoří mapování mezi alias "SHA256CSP" a zadaná adresa URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm).  
  
 K registraci algoritmus vlastní kód používá <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> metoda. Tato metoda vytvoří obou mapování. Následující příklad ukazuje způsob volání této metody:  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Konfiguraci vazby  
 Konfiguraci vazby zadáním vlastní <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-odvozené třídy v závazné nastavení, jak je znázorněno v následující fragment kódu:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Úplný příklad, naleznete v tématu [kryptografická flexibilita v zabezpečení WCF](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) ukázka.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpečení služeb](../../../../docs/framework/wcf/securing-services.md)  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)
