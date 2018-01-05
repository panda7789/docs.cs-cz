---
title: "Mapování názvů algoritmů na třídy šifrování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9c9c5b1f69200d4ee5d39c98445b668813718dd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="56c64-102">Mapování názvů algoritmů na třídy šifrování</span><span class="sxs-lookup"><span data-stu-id="56c64-102">Mapping Algorithm Names to Cryptography Classes</span></span>
<span data-ttu-id="56c64-103">Existují čtyři způsoby Vývojář můžete vytvořit objekt šifrování pomocí [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="56c64-103">There are four ways a developer can create a cryptography object using the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:</span></span>  
  
-   <span data-ttu-id="56c64-104">Vytvoření objektu služby pomocí **nové** operátor.</span><span class="sxs-lookup"><span data-stu-id="56c64-104">Create an object by using the **new** operator.</span></span>  
  
-   <span data-ttu-id="56c64-105">Vytvoření objektu, který implementuje algoritmus šifrování konkrétní voláním **vytvořit** metodu pro abstraktní třídu pro tento algoritmus.</span><span class="sxs-lookup"><span data-stu-id="56c64-105">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
-   <span data-ttu-id="56c64-106">Vytvoření objektu, který implementuje algoritmus šifrování konkrétní voláním <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="56c64-106">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="56c64-107">Vytvoření objektu, který implementuje třídu kryptografické algoritmy (například symetrický bloku šifru) voláním **vytvořit** metodu pro abstraktní třídu pro tento typ algoritmu (například <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span><span class="sxs-lookup"><span data-stu-id="56c64-107">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="56c64-108">Předpokládejme například, že vývojář chce výpočetní algoritmus hash SHA1 sada bajtů.</span><span class="sxs-lookup"><span data-stu-id="56c64-108">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="56c64-109"><xref:System.Security.Cryptography> Obor názvů obsahuje dvě implementace algoritmus SHA1, jeden čistě spravované implementace a ten, který zabalí rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="56c64-109">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="56c64-110">Vývojář můžete vytvořit instanci konkrétní implementace SHA1 (například <xref:System.Security.Cryptography.SHA1Managed>) voláním **nové** operátor.</span><span class="sxs-lookup"><span data-stu-id="56c64-110">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="56c64-111">Pokud však není důležité, které třídy modulu CLR načte tak dlouho, dokud třída implementuje algoritmus hash SHA1, vývojář může vytvořit objekt voláním <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="56c64-111">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="56c64-112">Tato metoda volá **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, které musí vracet implementace algoritmu hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="56c64-112">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="56c64-113">Vývojář může také zavolat **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** proto, že ve výchozím nastavení, konfiguraci šifrování zahrnuje krátké názvy pro algoritmy dodaný v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="56c64-113">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="56c64-114">Pokud není důležité, který algoritmus hash se používá, můžete volat Vývojář <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> metoda, která vrátí objekt, který implementuje hash transformace.</span><span class="sxs-lookup"><span data-stu-id="56c64-114">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="56c64-115">Mapování názvů algoritmů v konfiguračních souborech</span><span class="sxs-lookup"><span data-stu-id="56c64-115">Mapping Algorithm Names in Configuration Files</span></span>  
 <span data-ttu-id="56c64-116">Ve výchozím nastavení, vrátí modul runtime <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> objekt pro všechny čtyři scénáře.</span><span class="sxs-lookup"><span data-stu-id="56c64-116">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="56c64-117">Počítač správce ale můžete změnit typ objektu, který vrátí metody v posledních dvou scénářů.</span><span class="sxs-lookup"><span data-stu-id="56c64-117">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="56c64-118">Chcete-li to provést, je nutné mapovat do třídy, na kterou chcete použít v konfiguračním souboru počítače (Machine.config) algoritmus popisný název.</span><span class="sxs-lookup"><span data-stu-id="56c64-118">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="56c64-119">Následující příklad ukazuje, jak nakonfigurovat modul runtime, aby **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, a  **System.Security.Cryptography.HashAlgorithm.Create** vrátit `MySHA1HashClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="56c64-119">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
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
  
 <span data-ttu-id="56c64-120">Můžete zadat název atributu v [< cryptoclass –\> element](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (předchozí příklad názvy atribut `MySHA1Hash`).</span><span class="sxs-lookup"><span data-stu-id="56c64-120">You can specify the name of the attribute in the [<cryptoClass\> element](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="56c64-121">Hodnota atributu v  **\<cryptoclass – >** element je řetězec, který modul common language runtime používá k nalezení třídy.</span><span class="sxs-lookup"><span data-stu-id="56c64-121">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="56c64-122">Můžete použít libovolný řetězec, který splňuje požadavky uvedené v [určení plně kvalifikované názvy typů](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="56c64-122">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="56c64-123">Mnoho názvů algoritmů namapovat na stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="56c64-123">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="56c64-124">[ \<NameEntry > element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) mapuje třídu jeden algoritmus popisný název.</span><span class="sxs-lookup"><span data-stu-id="56c64-124">The [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="56c64-125">**Název** atribut může být buď řetězec, který se používá při volání metody **System.Security.Cryptography.CryptoConfig.CreateFromName** metoda nebo název třídy abstraktní kryptografie v <xref:System.Security.Cryptography> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="56c64-125">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="56c64-126">Hodnota **třída** atribut je název atributu v  **\<cryptoclass – >** element.</span><span class="sxs-lookup"><span data-stu-id="56c64-126">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56c64-127">Můžete získat algoritmus SHA1 voláním <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> nebo **Security.CryptoConfig.CreateFromName("SHA1")** metoda.</span><span class="sxs-lookup"><span data-stu-id="56c64-127">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="56c64-128">Každá metoda pouze zaručuje, že vrátí objekt, který implementuje algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="56c64-128">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="56c64-129">Nemáte k mapování jednotlivých popisný název algoritmu na stejnou třídu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="56c64-129">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="56c64-130">Seznam výchozích názvů a třídy jsou mapovány najdete v tématu <xref:System.Security.Cryptography.CryptoConfig>.</span><span class="sxs-lookup"><span data-stu-id="56c64-130">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c64-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="56c64-131">See Also</span></span>  
 [<span data-ttu-id="56c64-132">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="56c64-132">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="56c64-133">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="56c64-133">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
