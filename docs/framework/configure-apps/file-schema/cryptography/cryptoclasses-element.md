---
title: '&lt;cryptoClasses&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 85e47830649b0088d1e1645d73c4fb924ba5591f
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083324"
---
# <a name="ltcryptoclassesgt-element"></a><span data-ttu-id="ad8e0-102">&lt;cryptoClasses&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="ad8e0-102">&lt;cryptoClasses&gt; Element</span></span>
<span data-ttu-id="ad8e0-103">Obsahuje seznam šifrovacích tříd, které mají na popisný název v mapování [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="ad8e0-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="ad8e0-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="ad8e0-104">\<configuration></span></span>  
<span data-ttu-id="ad8e0-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="ad8e0-105">\<mscorlib></span></span>  
<span data-ttu-id="ad8e0-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="ad8e0-106">\<cryptographySettings></span></span>  
<span data-ttu-id="ad8e0-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="ad8e0-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="ad8e0-108">\<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="ad8e0-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad8e0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad8e0-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad8e0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ad8e0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ad8e0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ad8e0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad8e0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="ad8e0-112">Attributes</span></span>  
 <span data-ttu-id="ad8e0-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="ad8e0-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ad8e0-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ad8e0-114">Child Elements</span></span>  
  
|<span data-ttu-id="ad8e0-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="ad8e0-115">Element</span></span>|<span data-ttu-id="ad8e0-116">Popis</span><span class="sxs-lookup"><span data-stu-id="ad8e0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad8e0-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="ad8e0-117">\<cryptoClass></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="ad8e0-118">Obsahuje kryptografickou třídu, která nemá mapování na popisný název v  **\<nameEntry >** elementu.</span><span class="sxs-lookup"><span data-stu-id="ad8e0-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad8e0-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ad8e0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ad8e0-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="ad8e0-120">Element</span></span>|<span data-ttu-id="ad8e0-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ad8e0-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ad8e0-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad8e0-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ad8e0-123">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="ad8e0-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="ad8e0-124">Obsahuje mapování tříd pro popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="ad8e0-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="ad8e0-125">Obsahuje `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="ad8e0-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ad8e0-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad8e0-126">Example</span></span>  
 <span data-ttu-id="ad8e0-127">Následující příklad ukazuje způsob použití  **\<cryptoclass – >** element tak, aby odkazovaly kryptografickou třídu a konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ad8e0-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ad8e0-128">Můžete poté předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použití <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu pro návrat `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="ad8e0-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad8e0-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad8e0-129">See also</span></span>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="ad8e0-130">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ad8e0-130">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ad8e0-131">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="ad8e0-131">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="ad8e0-132">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="ad8e0-132">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="ad8e0-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="ad8e0-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [<span data-ttu-id="ad8e0-134">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="ad8e0-134">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
