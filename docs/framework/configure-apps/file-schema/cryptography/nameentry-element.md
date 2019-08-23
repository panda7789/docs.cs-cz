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
ms.openlocfilehash: d8f4d4aa9c80990cdf858da9fcdf6465438866cf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927564"
---
# <a name="nameentry-element"></a><span data-ttu-id="18771-102">\<nameEntry – element ></span><span class="sxs-lookup"><span data-stu-id="18771-102">\<nameEntry> Element</span></span>
<span data-ttu-id="18771-103">Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.</span><span class="sxs-lookup"><span data-stu-id="18771-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="18771-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="18771-104">\<configuration></span></span>  
<span data-ttu-id="18771-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="18771-105">\<mscorlib></span></span>  
<span data-ttu-id="18771-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="18771-106">\<cryptographySettings></span></span>  
<span data-ttu-id="18771-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="18771-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="18771-108">\<nameEntry ></span><span class="sxs-lookup"><span data-stu-id="18771-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18771-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18771-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18771-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="18771-110">Attributes and Elements</span></span>  
 <span data-ttu-id="18771-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="18771-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18771-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="18771-112">Attributes</span></span>  
  
|<span data-ttu-id="18771-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="18771-113">Attribute</span></span>|<span data-ttu-id="18771-114">Popis</span><span class="sxs-lookup"><span data-stu-id="18771-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18771-115">**name**</span><span class="sxs-lookup"><span data-stu-id="18771-115">**name**</span></span>|<span data-ttu-id="18771-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="18771-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="18771-117">Určuje popisný název algoritmu, který kryptografická třída implementuje.</span><span class="sxs-lookup"><span data-stu-id="18771-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="18771-118">**class**</span><span class="sxs-lookup"><span data-stu-id="18771-118">**class**</span></span>|<span data-ttu-id="18771-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="18771-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="18771-120">Určuje hodnotu atributu **Name** v [ \<elementu cryptoClass >](cryptoclass-element.md) .</span><span class="sxs-lookup"><span data-stu-id="18771-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18771-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="18771-121">Child Elements</span></span>  
 <span data-ttu-id="18771-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="18771-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18771-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="18771-123">Parent Elements</span></span>  
  
|<span data-ttu-id="18771-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="18771-124">Element</span></span>|<span data-ttu-id="18771-125">Popis</span><span class="sxs-lookup"><span data-stu-id="18771-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="18771-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18771-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="18771-127">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="18771-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18771-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18771-128">Remarks</span></span>  
 <span data-ttu-id="18771-129">Atribut **Name** může být název jedné z abstraktních tříd nalezených v <xref:System.Security.Cryptography> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="18771-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="18771-130">Při volání metody **Create** na abstraktní kryptografické třídě je název abstraktní třídy předán <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="18771-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="18771-131">**CreateFromName** vrací instanci typu, která je označena atributem **Class** .</span><span class="sxs-lookup"><span data-stu-id="18771-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="18771-132">Pokud je atribut **Name** krátkým názvem, jako je například RSA, můžete použít tento název při volání metody **CreateFromName** .</span><span class="sxs-lookup"><span data-stu-id="18771-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18771-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="18771-133">Example</span></span>  
 <span data-ttu-id="18771-134">Následující příklad ukazuje způsob použití  **\<prvku nameEntry >** k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="18771-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="18771-135">Pak můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě a <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> použít metodu k vrácení `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="18771-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18771-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18771-136">See also</span></span>

- [<span data-ttu-id="18771-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="18771-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="18771-138">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="18771-138">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="18771-139">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="18771-139">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="18771-140">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="18771-140">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
