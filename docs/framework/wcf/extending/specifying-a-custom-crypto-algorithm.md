---
title: Určení vlastního šifrovacího algoritmu
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: c92ce463f885e9784913b07eb11941ecd7d78d09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113708"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="c1993-102">Určení vlastního šifrovacího algoritmu</span><span class="sxs-lookup"><span data-stu-id="c1993-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="c1993-103">WCF umožňuje určení vlastního šifrovacího algoritmu, který chcete použít, pokud k šifrování dat nebo výpočetní digitální podpisy.</span><span class="sxs-lookup"><span data-stu-id="c1993-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="c1993-104">Uděláte to pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="c1993-104">This is done by the following steps:</span></span>  
  
1.  <span data-ttu-id="c1993-105">Odvodit třídu z</span><span class="sxs-lookup"><span data-stu-id="c1993-105">Derive a class from</span></span> <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2.  <span data-ttu-id="c1993-106">Zaregistrujte algoritmus</span><span class="sxs-lookup"><span data-stu-id="c1993-106">Register the algorithm</span></span>  
  
3.  <span data-ttu-id="c1993-107">Konfigurace vazby s <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="c1993-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="c1993-108">Odvodit třídu z SecurityAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="c1993-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="c1993-109"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Je abstraktní základní třída, která vám umožní určit algoritmus pro použití při provádění zabezpečení různých operací souvisejících s.</span><span class="sxs-lookup"><span data-stu-id="c1993-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="c1993-110">Například výpočtu hodnoty hash pro digitální podpis nebo šifrování zprávy.</span><span class="sxs-lookup"><span data-stu-id="c1993-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="c1993-111">Následující kód ukazuje, jak odvodit třídu z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span><span class="sxs-lookup"><span data-stu-id="c1993-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
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
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="c1993-112">Registrace vlastního algoritmu</span><span class="sxs-lookup"><span data-stu-id="c1993-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="c1993-113">Registrace může provést, v konfiguračním souboru nebo imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="c1993-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="c1993-114">Registrace vlastního algoritmu se provádí tak, že vytvoříte mapování mezi třídy implementující zprostředkovatele kryptografických služeb a alias.</span><span class="sxs-lookup"><span data-stu-id="c1993-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="c1993-115">Alias se pak namapuje na identifikátor URI, který se používá při určování algoritmus ve vazbě služby WCF.</span><span class="sxs-lookup"><span data-stu-id="c1993-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="c1993-116">Následující konfigurace fragment kódu ukazuje, jak zaregistrovat vlastní algoritmus v konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="c1993-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
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
  
 <span data-ttu-id="c1993-117">Části <`cryptoClasses`> element vytvoří mapování mezi SHA256CryptoServiceProvider a alias "SHA256CSP".</span><span class="sxs-lookup"><span data-stu-id="c1993-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="c1993-118"><`nameEntry`> Element vytvoří mapování mezi "SHA256CSP" alias a zadaná adresa URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span><span class="sxs-lookup"><span data-stu-id="c1993-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span></span>  
  
 <span data-ttu-id="c1993-119">K registraci vlastního algoritmu kód používá <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> metody.</span><span class="sxs-lookup"><span data-stu-id="c1993-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="c1993-120">Tato metoda vytvoří oba mapování.</span><span class="sxs-lookup"><span data-stu-id="c1993-120">This method creates both mappings.</span></span> <span data-ttu-id="c1993-121">Následující příklad ukazuje, jak volat tuto metodu:</span><span class="sxs-lookup"><span data-stu-id="c1993-121">The following example shows how to call this method:</span></span>  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="c1993-122">Konfiguraci vazby</span><span class="sxs-lookup"><span data-stu-id="c1993-122">Configure the Binding</span></span>  
 <span data-ttu-id="c1993-123">Konfiguraci vazby tak, že zadáte vlastní <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-odvozené třídy v nastavení vazby, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="c1993-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="c1993-124">Kompletní příklad, najdete v článku [kryptografická flexibilita v zabezpečení WCF](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="c1993-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1993-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1993-125">See also</span></span>

- [<span data-ttu-id="c1993-126">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c1993-126">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c1993-127">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="c1993-127">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="c1993-128">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c1993-128">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="c1993-129">Koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c1993-129">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)
