---
title: '&lt;nameEntry&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a4c29db3f84570d4d5e99a1deaf8beb3145c8ea1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626937"
---
# <a name="ltnameentrygt-element"></a><span data-ttu-id="4c5c7-102">&lt;nameEntry&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="4c5c7-102">&lt;nameEntry&gt; Element</span></span>
<span data-ttu-id="4c5c7-103">Název třídy mapuje na algoritmus popisný název, který umožňuje jedna třída má mnoho popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="4c5c7-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="4c5c7-104">\<configuration></span></span>  
<span data-ttu-id="4c5c7-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="4c5c7-105">\<mscorlib></span></span>  
<span data-ttu-id="4c5c7-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="4c5c7-106">\<cryptographySettings></span></span>  
<span data-ttu-id="4c5c7-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="4c5c7-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="4c5c7-108">\<nameEntry – ></span><span class="sxs-lookup"><span data-stu-id="4c5c7-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c5c7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c5c7-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c5c7-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4c5c7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4c5c7-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c5c7-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4c5c7-112">Attributes</span></span>  
  
|<span data-ttu-id="4c5c7-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="4c5c7-113">Attribute</span></span>|<span data-ttu-id="4c5c7-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4c5c7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c5c7-115">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="4c5c7-115">**name**</span></span>|<span data-ttu-id="4c5c7-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="4c5c7-117">Určuje popisný název algoritmu, který implementuje kryptografickou třídu.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="4c5c7-118">**class**</span><span class="sxs-lookup"><span data-stu-id="4c5c7-118">**class**</span></span>|<span data-ttu-id="4c5c7-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="4c5c7-120">Určuje hodnotu **název** atribut [ \<cryptoclass – >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c5c7-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4c5c7-121">Child Elements</span></span>  
 <span data-ttu-id="4c5c7-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="4c5c7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c5c7-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4c5c7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4c5c7-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="4c5c7-124">Element</span></span>|<span data-ttu-id="4c5c7-125">Popis</span><span class="sxs-lookup"><span data-stu-id="4c5c7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4c5c7-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="4c5c7-127">Určuje kořenový element části o konfiguraci technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c5c7-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c5c7-128">Remarks</span></span>  
 <span data-ttu-id="4c5c7-129">**Název** atribut může být název jedné z abstraktní třídy součástí <xref:System.Security.Cryptography> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="4c5c7-130">Při volání **vytvořit** metoda abstract kryptografickou třídu, název abstraktní třídy je předán <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="4c5c7-131">**CreateFromName** vrací instanci typu indikován **třídy** atribut.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="4c5c7-132">Pokud **název** atribut je krátký název, třeba RSA, můžete použít tento název při volání **CreateFromName** metoda.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c5c7-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c5c7-133">Example</span></span>  
 <span data-ttu-id="4c5c7-134">Následující příklad ukazuje způsob použití  **\<nameEntry >** element tak, aby odkazovaly kryptografickou třídu a konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="4c5c7-135">Můžete poté předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použití <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu pro návrat `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="4c5c7-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4c5c7-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c5c7-136">See also</span></span>
- [<span data-ttu-id="4c5c7-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="4c5c7-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="4c5c7-138">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="4c5c7-138">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="4c5c7-139">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="4c5c7-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="4c5c7-140">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="4c5c7-140">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
