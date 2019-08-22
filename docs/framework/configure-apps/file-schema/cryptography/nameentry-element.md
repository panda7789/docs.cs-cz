---
title: Element <nameEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 9270552245b3867f0f09741ded3f9da6a8b6c135
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664268"
---
# <a name="nameentry-element"></a><span data-ttu-id="565c4-102">\<nameEntry – element ></span><span class="sxs-lookup"><span data-stu-id="565c4-102">\<nameEntry> Element</span></span>
<span data-ttu-id="565c4-103">Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.</span><span class="sxs-lookup"><span data-stu-id="565c4-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="565c4-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="565c4-104">\<configuration></span></span>  
<span data-ttu-id="565c4-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="565c4-105">\<mscorlib></span></span>  
<span data-ttu-id="565c4-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="565c4-106">\<cryptographySettings></span></span>  
<span data-ttu-id="565c4-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="565c4-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="565c4-108">\<nameEntry ></span><span class="sxs-lookup"><span data-stu-id="565c4-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="565c4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="565c4-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="565c4-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="565c4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="565c4-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="565c4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="565c4-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="565c4-112">Attributes</span></span>  
  
|<span data-ttu-id="565c4-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="565c4-113">Attribute</span></span>|<span data-ttu-id="565c4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="565c4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="565c4-115">**name**</span><span class="sxs-lookup"><span data-stu-id="565c4-115">**name**</span></span>|<span data-ttu-id="565c4-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="565c4-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="565c4-117">Určuje popisný název algoritmu, který kryptografická třída implementuje.</span><span class="sxs-lookup"><span data-stu-id="565c4-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="565c4-118">**class**</span><span class="sxs-lookup"><span data-stu-id="565c4-118">**class**</span></span>|<span data-ttu-id="565c4-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="565c4-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="565c4-120">Určuje hodnotu atributu **Name** v [ \<elementu cryptoClass >](cryptoclass-element.md) .</span><span class="sxs-lookup"><span data-stu-id="565c4-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="565c4-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="565c4-121">Child Elements</span></span>  
 <span data-ttu-id="565c4-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="565c4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="565c4-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="565c4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="565c4-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="565c4-124">Element</span></span>|<span data-ttu-id="565c4-125">Popis</span><span class="sxs-lookup"><span data-stu-id="565c4-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="565c4-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="565c4-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="565c4-127">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="565c4-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="565c4-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="565c4-128">Remarks</span></span>  
 <span data-ttu-id="565c4-129">Atribut **Name** může být název jedné z abstraktních tříd nalezených v <xref:System.Security.Cryptography> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="565c4-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="565c4-130">Při volání metody **Create** na abstraktní kryptografické třídě je název abstraktní třídy předán <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="565c4-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="565c4-131">**CreateFromName** vrací instanci typu, která je označena atributem **Class** .</span><span class="sxs-lookup"><span data-stu-id="565c4-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="565c4-132">Pokud je atribut **Name** krátkým názvem, jako je například RSA, můžete použít tento název při volání metody **CreateFromName** .</span><span class="sxs-lookup"><span data-stu-id="565c4-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="565c4-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="565c4-133">Example</span></span>  
 <span data-ttu-id="565c4-134">Následující příklad ukazuje způsob použití  **\<prvku nameEntry >** k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="565c4-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="565c4-135">Pak můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě a <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> použít metodu k vrácení `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="565c4-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="565c4-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="565c4-136">See also</span></span>

- [<span data-ttu-id="565c4-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="565c4-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="565c4-138">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="565c4-138">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="565c4-139">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="565c4-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="565c4-140">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="565c4-140">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
