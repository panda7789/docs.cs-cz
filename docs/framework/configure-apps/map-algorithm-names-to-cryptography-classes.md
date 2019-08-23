---
title: Mapování názvů algoritmů na třídy šifrování
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 513000169504473aa6dd46feaca214f58502ffd0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912871"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="d4020-102">Mapování názvů algoritmů na třídy šifrování</span><span class="sxs-lookup"><span data-stu-id="d4020-102">Mapping Algorithm Names to Cryptography Classes</span></span>
<span data-ttu-id="d4020-103">Existují čtyři způsoby, jak může vývojář vytvořit objekt kryptografie pomocí Windows SDK:</span><span class="sxs-lookup"><span data-stu-id="d4020-103">There are four ways a developer can create a cryptography object using the Windows SDK:</span></span>  
  
- <span data-ttu-id="d4020-104">Vytvořte objekt pomocí operátoru **New** .</span><span class="sxs-lookup"><span data-stu-id="d4020-104">Create an object by using the **new** operator.</span></span>  
  
- <span data-ttu-id="d4020-105">Vytvořte objekt, který implementuje konkrétní kryptografický algoritmus, voláním metody **Create** pro abstraktní třídu pro daný algoritmus.</span><span class="sxs-lookup"><span data-stu-id="d4020-105">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
- <span data-ttu-id="d4020-106">Vytvořte objekt, který implementuje určitý kryptografický algoritmus voláním <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d4020-106">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="d4020-107">Vytvořte objekt, který implementuje třídu kryptografických algoritmů (například symetrického bloku Block), voláním metody **Create** pro abstraktní třídu pro daný typ algoritmu (například <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span><span class="sxs-lookup"><span data-stu-id="d4020-107">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="d4020-108">Předpokládejme například, že vývojář chce vypočítat hodnotu hash SHA1 sady bajtů.</span><span class="sxs-lookup"><span data-stu-id="d4020-108">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="d4020-109"><xref:System.Security.Cryptography> Obor názvů obsahuje dvě implementace algoritmu SHA1, jednu čistě spravovanou implementaci a jednu, která zabalí rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="d4020-109">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="d4020-110">Vývojář se může rozhodnout pro vytvoření instance konkrétní implementace SHA1 (například <xref:System.Security.Cryptography.SHA1Managed>) voláním operátoru **New** .</span><span class="sxs-lookup"><span data-stu-id="d4020-110">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="d4020-111">Pokud se však nezáleží na tom, jakou třídu modul CLR (Common Language Runtime) načítá, pokud třída implementuje algoritmus hash SHA1, může vývojář vytvořit objekt voláním <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d4020-111">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d4020-112">Tato metoda volá **System. Security. Cryptography. objektu CryptoConfig. CreateFromName ("System. Security. Cryptography. SHA1")** , která musí vracet implementaci algoritmu hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="d4020-112">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="d4020-113">Vývojář může také volat **System. Security. Cryptography. objektu CryptoConfig. CreateFromName ("SHA1")** , protože ve výchozím nastavení konfigurace kryptografie obsahuje krátké názvy pro algoritmy dodávané v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d4020-113">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="d4020-114">Pokud nezáleží na tom, který algoritmus hash je použit, může vývojář zavolat <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> metodu, která vrátí objekt, který implementuje transformaci hash.</span><span class="sxs-lookup"><span data-stu-id="d4020-114">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="d4020-115">Mapování názvů algoritmů v konfiguračních souborech</span><span class="sxs-lookup"><span data-stu-id="d4020-115">Mapping Algorithm Names in Configuration Files</span></span>  
 <span data-ttu-id="d4020-116">Ve výchozím nastavení vrátí <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> modul runtime objekt pro všechny čtyři scénáře.</span><span class="sxs-lookup"><span data-stu-id="d4020-116">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="d4020-117">Správce počítače však může změnit typ objektu, který metody v posledních dvou scénářích vrátí.</span><span class="sxs-lookup"><span data-stu-id="d4020-117">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="d4020-118">K tomu je nutné namapovat popisný název algoritmu na třídu, kterou chcete použít v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="d4020-118">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="d4020-119">Následující příklad ukazuje, jak nakonfigurovat modul runtime tak, aby byl **System. Security. Cryptography. SHA1. Create**, **System. Security. objektu CryptoConfig. CREATEFROMNAME ("SHA1")** a **System. Security. Cryptography. HashAlgorithm. Create Vrátí objekt.** `MySHA1HashClass`</span><span class="sxs-lookup"><span data-stu-id="d4020-119">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="d4020-120">Můžete zadat název atributu v [elementu < cryptoClass\> ](./file-schema/cryptography/cryptoclass-element.md) (předchozí příklad název atributu `MySHA1Hash`).</span><span class="sxs-lookup"><span data-stu-id="d4020-120">You can specify the name of the attribute in the [<cryptoClass\> element](./file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="d4020-121">Hodnota atributu v  **\<prvku cryptoClass >** je řetězec, který modul CLR (Common Language Runtime) používá k nalezení třídy.</span><span class="sxs-lookup"><span data-stu-id="d4020-121">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="d4020-122">Můžete použít libovolný řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="d4020-122">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="d4020-123">Mnoho názvů algoritmů může být mapováno na stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="d4020-123">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="d4020-124">Element nameEntry > mapuje třídu na jeden popisný název algoritmu. [ \<](./file-schema/cryptography/nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="d4020-124">The [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="d4020-125">Atribut **Name** může být buď řetězec, který se používá při volání metody **System. Security. Cryptography. objektu CryptoConfig. CreateFromName** nebo názvu abstraktní <xref:System.Security.Cryptography> třídy kryptografie v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d4020-125">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="d4020-126">Hodnota atributu **Class** je název atributu v  **\<elementu cryptoClass >** .</span><span class="sxs-lookup"><span data-stu-id="d4020-126">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4020-127">Algoritmus SHA1 lze získat voláním <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metody nebo metody **Security. objektu CryptoConfig. CreateFromName ("SHA1")** .</span><span class="sxs-lookup"><span data-stu-id="d4020-127">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="d4020-128">Každá metoda zaručuje pouze to, že vrátí objekt, který implementuje algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="d4020-128">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="d4020-129">V konfiguračním souboru není nutné namapovat každý popisný název algoritmu na stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="d4020-129">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="d4020-130">Seznam výchozích názvů a tříd, na které se mapují, najdete v tématu <xref:System.Security.Cryptography.CryptoConfig>.</span><span class="sxs-lookup"><span data-stu-id="d4020-130">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4020-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4020-131">See also</span></span>

- [<span data-ttu-id="d4020-132">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="d4020-132">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="d4020-133">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="d4020-133">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
