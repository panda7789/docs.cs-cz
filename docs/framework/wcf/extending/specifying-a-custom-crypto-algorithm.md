---
title: Určení vlastního šifrovacího algoritmu
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: d8fb22daac66c3ef80f148db03703fc5024d3438
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489218"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="b280c-102">Určení vlastního šifrovacího algoritmu</span><span class="sxs-lookup"><span data-stu-id="b280c-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="b280c-103">WCF umožňuje zadat vlastního šifrovacího algoritmu, který má použít při šifrování dat nebo výpočetní digitální podpisy.</span><span class="sxs-lookup"><span data-stu-id="b280c-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="b280c-104">Uděláte to pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="b280c-104">This is done by the following steps:</span></span>  
  
1.  <span data-ttu-id="b280c-105">Odvození třídy z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="b280c-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2.  <span data-ttu-id="b280c-106">Zaregistrovat algoritmus</span><span class="sxs-lookup"><span data-stu-id="b280c-106">Register the algorithm</span></span>  
  
3.  <span data-ttu-id="b280c-107">Konfiguraci vazby s <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="b280c-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="b280c-108">Odvození třídy z SecurityAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="b280c-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="b280c-109"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Je abstraktní základní třída, která vám umožní určit, že algoritmus použije při provádění různých zabezpečení operací souvisejících s.</span><span class="sxs-lookup"><span data-stu-id="b280c-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="b280c-110">Například computing hodnotu hash pro digitální podpis nebo šifrování zprávy.</span><span class="sxs-lookup"><span data-stu-id="b280c-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="b280c-111">Následující kód ukazuje, jak na odvození třídy z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span><span class="sxs-lookup"><span data-stu-id="b280c-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
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
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="b280c-112">Zaregistrovat vlastní algoritmus</span><span class="sxs-lookup"><span data-stu-id="b280c-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="b280c-113">Registrace lze provést v konfiguračním souboru nebo v imperativní kódu.</span><span class="sxs-lookup"><span data-stu-id="b280c-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="b280c-114">Registrace vlastní algoritmus se provádí tak, že vytvoříte mapování mezi třídu, která implementuje zprostředkovatele kryptografických služeb a alias.</span><span class="sxs-lookup"><span data-stu-id="b280c-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="b280c-115">Alias je poté mapován na identifikátor URI, který se používá při zadávání algoritmus do vazby služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b280c-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="b280c-116">Následující fragment kódu konfigurace ukazuje, jak se zaregistrovat vlastní algoritmus v konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="b280c-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
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
  
 <span data-ttu-id="b280c-117">V části v rámci <`cryptoClasses`> element vytvoří mapování mezi SHA256CryptoServiceProvider a alias "SHA256CSP".</span><span class="sxs-lookup"><span data-stu-id="b280c-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="b280c-118"><`nameEntry`> Element vytvoří mapování mezi alias "SHA256CSP" a zadaná adresa URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span><span class="sxs-lookup"><span data-stu-id="b280c-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span></span>  
  
 <span data-ttu-id="b280c-119">K registraci algoritmus vlastní kód používá <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> metoda.</span><span class="sxs-lookup"><span data-stu-id="b280c-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="b280c-120">Tato metoda vytvoří obou mapování.</span><span class="sxs-lookup"><span data-stu-id="b280c-120">This method creates both mappings.</span></span> <span data-ttu-id="b280c-121">Následující příklad ukazuje způsob volání této metody:</span><span class="sxs-lookup"><span data-stu-id="b280c-121">The following example shows how to call this method:</span></span>  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="b280c-122">Konfiguraci vazby</span><span class="sxs-lookup"><span data-stu-id="b280c-122">Configure the Binding</span></span>  
 <span data-ttu-id="b280c-123">Konfiguraci vazby zadáním vlastní <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-odvozené třídy v závazné nastavení, jak je znázorněno v následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="b280c-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="b280c-124">Úplný příklad, naleznete v tématu [kryptografická flexibilita v zabezpečení WCF](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="b280c-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b280c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="b280c-125">See Also</span></span>  
 [<span data-ttu-id="b280c-126">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b280c-126">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="b280c-127">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="b280c-127">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="b280c-128">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b280c-128">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="b280c-129">Koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b280c-129">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)
