---
title: Určení vlastního šifrovacího algoritmu
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 0bfa6c46f4db1171eb314625e36c267000a0ec12
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628680"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="fbf8c-102">Určení vlastního šifrovacího algoritmu</span><span class="sxs-lookup"><span data-stu-id="fbf8c-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="fbf8c-103">WCF umožňuje zadat vlastní šifrovací algoritmus, který se použije při šifrování dat nebo výpočetních digitálních podpisů.</span><span class="sxs-lookup"><span data-stu-id="fbf8c-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="fbf8c-104">To se provádí pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="fbf8c-104">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="fbf8c-105">Odvodit třídu z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="fbf8c-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="fbf8c-106">Registrovat algoritmus</span><span class="sxs-lookup"><span data-stu-id="fbf8c-106">Register the algorithm</span></span>  
  
3. <span data-ttu-id="fbf8c-107">Nakonfigurujte vazbu s třídou odvozenou od <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="fbf8c-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="fbf8c-108">Odvození třídy z SecurityAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="fbf8c-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="fbf8c-109"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> je abstraktní základní třída, která umožňuje určit algoritmus, který se má použít při provádění různých operací souvisejících se zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="fbf8c-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="fbf8c-110">Například výpočet hash pro digitální podpis nebo šifrování zprávy.</span><span class="sxs-lookup"><span data-stu-id="fbf8c-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="fbf8c-111">Následující kód ukazuje, jak odvodit třídu z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span><span class="sxs-lookup"><span data-stu-id="fbf8c-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
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
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="fbf8c-112">Registrace vlastního algoritmu</span><span class="sxs-lookup"><span data-stu-id="fbf8c-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="fbf8c-113">Registraci je možné provést v konfiguračním souboru nebo v imperativně kódu.</span><span class="sxs-lookup"><span data-stu-id="fbf8c-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="fbf8c-114">Registrace vlastního algoritmu se provádí vytvořením mapování mezi třídou, která implementuje poskytovatele kryptografických služeb a aliasu.</span><span class="sxs-lookup"><span data-stu-id="fbf8c-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="fbf8c-115">Alias se pak namapuje na identifikátor URI, který se používá při zadávání algoritmu ve vazbě služby WCF.</span><span class="sxs-lookup"><span data-stu-id="fbf8c-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="fbf8c-116">Následující fragment kódu ukazuje, jak zaregistrovat vlastní algoritmus v konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="fbf8c-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
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
  
 <span data-ttu-id="fbf8c-117">Část pod prvkem <`cryptoClasses`> vytvoří mapování mezi SHA256CryptoServiceProvider a aliasem "SHA256CSP".</span><span class="sxs-lookup"><span data-stu-id="fbf8c-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="fbf8c-118">Element <`nameEntry`> vytvoří mapování mezi aliasem "SHA256CSP" a zadanou `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`ou URL.</span><span class="sxs-lookup"><span data-stu-id="fbf8c-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`.</span></span>  
  
 <span data-ttu-id="fbf8c-119">Chcete-li zaregistrovat vlastní algoritmus v kódu, použijte metodu <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="fbf8c-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="fbf8c-120">Tato metoda vytvoří obě mapování.</span><span class="sxs-lookup"><span data-stu-id="fbf8c-120">This method creates both mappings.</span></span> <span data-ttu-id="fbf8c-121">Následující příklad ukazuje, jak zavolat tuto metodu:</span><span class="sxs-lookup"><span data-stu-id="fbf8c-121">The following example shows how to call this method:</span></span>  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="fbf8c-122">Konfigurace vazby</span><span class="sxs-lookup"><span data-stu-id="fbf8c-122">Configure the Binding</span></span>  
 <span data-ttu-id="fbf8c-123">Vazbu nakonfigurujete tak, že v nastavení vazby zadáte vlastní třídu odvozenou od <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="fbf8c-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="fbf8c-124">Úplný příklad kódu naleznete [v tématu kryptografická flexibilita v ukázce zabezpečení služby WCF](../samples/cryptographic-agility-in-wcf-security.md) .</span><span class="sxs-lookup"><span data-stu-id="fbf8c-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf8c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbf8c-125">See also</span></span>

- [<span data-ttu-id="fbf8c-126">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="fbf8c-126">Securing Services and Clients</span></span>](../feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fbf8c-127">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="fbf8c-127">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="fbf8c-128">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fbf8c-128">Security Overview</span></span>](../feature-details/security-overview.md)
- [<span data-ttu-id="fbf8c-129">Koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fbf8c-129">Security Concepts</span></span>](../feature-details/security-concepts.md)
