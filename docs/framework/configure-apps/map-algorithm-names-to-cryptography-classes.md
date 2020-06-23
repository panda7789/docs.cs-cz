---
title: Mapování názvů algoritmů na třídy šifrování
description: Mapování názvů algoritmů na kryptografické třídy v rozhraní .NET. Vývojář má čtyři možnosti pro vytvoření objektu kryptografie.
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 5a1d7acdd34182dd82f4dce66d136c4ef4de6e95
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105356"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="696ec-104">Mapování názvů algoritmů na třídy šifrování</span><span class="sxs-lookup"><span data-stu-id="696ec-104">Mapping Algorithm Names to Cryptography Classes</span></span>
<span data-ttu-id="696ec-105">Existují čtyři způsoby, jak může vývojář vytvořit objekt kryptografie pomocí Windows SDK:</span><span class="sxs-lookup"><span data-stu-id="696ec-105">There are four ways a developer can create a cryptography object using the Windows SDK:</span></span>  
  
- <span data-ttu-id="696ec-106">Vytvořte objekt pomocí operátoru **New** .</span><span class="sxs-lookup"><span data-stu-id="696ec-106">Create an object by using the **new** operator.</span></span>  
  
- <span data-ttu-id="696ec-107">Vytvořte objekt, který implementuje konkrétní kryptografický algoritmus, voláním metody **Create** pro abstraktní třídu pro daný algoritmus.</span><span class="sxs-lookup"><span data-stu-id="696ec-107">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
- <span data-ttu-id="696ec-108">Vytvořte objekt, který implementuje určitý kryptografický algoritmus voláním <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="696ec-108">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="696ec-109">Vytvořte objekt, který implementuje třídu kryptografických algoritmů (například symetrického bloku Block), voláním metody **Create** pro abstraktní třídu pro daný typ algoritmu (například <xref:System.Security.Cryptography.SymmetricAlgorithm> ).</span><span class="sxs-lookup"><span data-stu-id="696ec-109">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="696ec-110">Předpokládejme například, že vývojář chce vypočítat hodnotu hash SHA1 sady bajtů.</span><span class="sxs-lookup"><span data-stu-id="696ec-110">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="696ec-111"><xref:System.Security.Cryptography>Obor názvů obsahuje dvě implementace algoritmu SHA1, jednu čistě spravovanou implementaci a jednu, která zabalí rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="696ec-111">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="696ec-112">Vývojář se může rozhodnout pro vytvoření instance konkrétní implementace SHA1 (například <xref:System.Security.Cryptography.SHA1Managed> ) voláním operátoru **New** .</span><span class="sxs-lookup"><span data-stu-id="696ec-112">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="696ec-113">Pokud se však nezáleží na tom, jakou třídu modul CLR (Common Language Runtime) načítá, pokud třída implementuje algoritmus hash SHA1, může vývojář vytvořit objekt voláním <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="696ec-113">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="696ec-114">Tato metoda volá **System. Security. Cryptography. objektu CryptoConfig. CreateFromName ("System. Security. Cryptography. SHA1")**, která musí vracet implementaci algoritmu hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="696ec-114">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="696ec-115">Vývojář může také volat **System. Security. Cryptography. objektu CryptoConfig. CreateFromName ("SHA1")** , protože ve výchozím nastavení konfigurace kryptografie obsahuje krátké názvy pro algoritmy dodávané v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="696ec-115">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="696ec-116">Pokud nezáleží na tom, který algoritmus hash je použit, může vývojář zavolat <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> metodu, která vrátí objekt, který implementuje transformaci hash.</span><span class="sxs-lookup"><span data-stu-id="696ec-116">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="696ec-117">Mapování názvů algoritmů v konfiguračních souborech</span><span class="sxs-lookup"><span data-stu-id="696ec-117">Mapping Algorithm Names in Configuration Files</span></span>  
 <span data-ttu-id="696ec-118">Ve výchozím nastavení vrátí modul runtime <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> objekt pro všechny čtyři scénáře.</span><span class="sxs-lookup"><span data-stu-id="696ec-118">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="696ec-119">Správce počítače však může změnit typ objektu, který metody v posledních dvou scénářích vrátí.</span><span class="sxs-lookup"><span data-stu-id="696ec-119">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="696ec-120">K tomu je nutné namapovat popisný název algoritmu na třídu, kterou chcete použít v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="696ec-120">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="696ec-121">Následující příklad ukazuje, jak konfigurovat modul runtime tak, aby **System. Security. Cryptography. SHA1. Create**, **System. Security. objektu CryptoConfig. CREATEFROMNAME ("SHA1")** a **System. Security. Cryptography. HashAlgorithm. Create** vrátil `MySHA1HashClass` objekt.</span><span class="sxs-lookup"><span data-stu-id="696ec-121">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
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
  
 <span data-ttu-id="696ec-122">Můžete zadat název atributu v [ \> elementu<cryptoClass](./file-schema/cryptography/cryptoclass-element.md) (předchozí příklad název atributu `MySHA1Hash` ).</span><span class="sxs-lookup"><span data-stu-id="696ec-122">You can specify the name of the attribute in the [<cryptoClass\> element](./file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="696ec-123">Hodnota atributu v **\<cryptoClass>** elementu je řetězec, který modul CLR (Common Language Runtime) používá k nalezení třídy.</span><span class="sxs-lookup"><span data-stu-id="696ec-123">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="696ec-124">Můžete použít libovolný řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="696ec-124">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="696ec-125">Mnoho názvů algoritmů může být mapováno na stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="696ec-125">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="696ec-126">[ \<nameEntry> Element](./file-schema/cryptography/nameentry-element.md) mapuje třídu na jeden popisný název algoritmu.</span><span class="sxs-lookup"><span data-stu-id="696ec-126">The [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="696ec-127">Atribut **Name** může být buď řetězec, který se používá při volání metody **System. Security. Cryptography. objektu CryptoConfig. CreateFromName** nebo názvu abstraktní třídy kryptografie v <xref:System.Security.Cryptography> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="696ec-127">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="696ec-128">Hodnota atributu **Class** je název atributu v **\<cryptoClass>** elementu.</span><span class="sxs-lookup"><span data-stu-id="696ec-128">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="696ec-129">Algoritmus SHA1 lze získat voláním <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metody nebo metody **Security. objektu CryptoConfig. CreateFromName ("SHA1")** .</span><span class="sxs-lookup"><span data-stu-id="696ec-129">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="696ec-130">Každá metoda zaručuje pouze to, že vrátí objekt, který implementuje algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="696ec-130">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="696ec-131">V konfiguračním souboru není nutné namapovat každý popisný název algoritmu na stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="696ec-131">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="696ec-132">Seznam výchozích názvů a tříd, na které se mapují, najdete v tématu <xref:System.Security.Cryptography.CryptoConfig> .</span><span class="sxs-lookup"><span data-stu-id="696ec-132">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696ec-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="696ec-133">See also</span></span>

- [<span data-ttu-id="696ec-134">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="696ec-134">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="696ec-135">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="696ec-135">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
