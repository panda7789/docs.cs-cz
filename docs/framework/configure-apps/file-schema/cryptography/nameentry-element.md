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
ms.openlocfilehash: 97521ba9073820beeea62f5fc7cab480b5422fb0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225323"
---
# <a name="nameentry-element"></a><span data-ttu-id="91b48-102">\<nameEntry – > – Element</span><span class="sxs-lookup"><span data-stu-id="91b48-102">\<nameEntry> Element</span></span>
<span data-ttu-id="91b48-103">Název třídy mapuje na algoritmus popisný název, který umožňuje jedna třída má mnoho popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="91b48-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="91b48-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="91b48-104">\<configuration></span></span>  
<span data-ttu-id="91b48-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="91b48-105">\<mscorlib></span></span>  
<span data-ttu-id="91b48-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="91b48-106">\<cryptographySettings></span></span>  
<span data-ttu-id="91b48-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="91b48-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="91b48-108">\<nameEntry – ></span><span class="sxs-lookup"><span data-stu-id="91b48-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91b48-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91b48-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91b48-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="91b48-110">Attributes and Elements</span></span>  
 <span data-ttu-id="91b48-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="91b48-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91b48-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="91b48-112">Attributes</span></span>  
  
|<span data-ttu-id="91b48-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="91b48-113">Attribute</span></span>|<span data-ttu-id="91b48-114">Popis</span><span class="sxs-lookup"><span data-stu-id="91b48-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91b48-115">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="91b48-115">**name**</span></span>|<span data-ttu-id="91b48-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="91b48-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="91b48-117">Určuje popisný název algoritmu, který implementuje kryptografickou třídu.</span><span class="sxs-lookup"><span data-stu-id="91b48-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="91b48-118">**class**</span><span class="sxs-lookup"><span data-stu-id="91b48-118">**class**</span></span>|<span data-ttu-id="91b48-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="91b48-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="91b48-120">Určuje hodnotu **název** atribut [ \<cryptoclass – >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="91b48-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91b48-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="91b48-121">Child Elements</span></span>  
 <span data-ttu-id="91b48-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="91b48-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91b48-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="91b48-123">Parent Elements</span></span>  
  
|<span data-ttu-id="91b48-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="91b48-124">Element</span></span>|<span data-ttu-id="91b48-125">Popis</span><span class="sxs-lookup"><span data-stu-id="91b48-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="91b48-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91b48-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="91b48-127">Určuje kořenový element části o konfiguraci technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="91b48-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91b48-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91b48-128">Remarks</span></span>  
 <span data-ttu-id="91b48-129">**Název** atribut může být název jedné z abstraktní třídy součástí <xref:System.Security.Cryptography> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="91b48-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="91b48-130">Při volání **vytvořit** metoda abstract kryptografickou třídu, název abstraktní třídy je předán <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="91b48-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="91b48-131">**CreateFromName** vrací instanci typu indikován **třídy** atribut.</span><span class="sxs-lookup"><span data-stu-id="91b48-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="91b48-132">Pokud **název** atribut je krátký název, třeba RSA, můžete použít tento název při volání **CreateFromName** metoda.</span><span class="sxs-lookup"><span data-stu-id="91b48-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91b48-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="91b48-133">Example</span></span>  
 <span data-ttu-id="91b48-134">Následující příklad ukazuje způsob použití  **\<nameEntry >** element tak, aby odkazovaly kryptografickou třídu a konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="91b48-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="91b48-135">Můžete poté předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použití <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu pro návrat `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="91b48-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91b48-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91b48-136">See also</span></span>

- [<span data-ttu-id="91b48-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="91b48-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="91b48-138">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="91b48-138">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="91b48-139">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="91b48-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="91b48-140">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="91b48-140">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
