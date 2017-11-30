---
title: "&lt;cryptoNameMapping –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2156c6441190b530c48a70e67e93e4806d20b199
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcryptonamemappinggt-element"></a><span data-ttu-id="04315-102">&lt;cryptoNameMapping –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="04315-102">&lt;cryptoNameMapping&gt; Element</span></span>
<span data-ttu-id="04315-103">Obsahuje mapování třídy popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="04315-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="04315-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="04315-104">\<configuration></span></span>  
<span data-ttu-id="04315-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="04315-105">\<mscorlib></span></span>  
<span data-ttu-id="04315-106">\<cryptographySettings – ></span><span class="sxs-lookup"><span data-stu-id="04315-106">\<cryptographySettings></span></span>  
<span data-ttu-id="04315-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="04315-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04315-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04315-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04315-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="04315-109">Attributes and Elements</span></span>  
 <span data-ttu-id="04315-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="04315-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04315-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="04315-111">Attributes</span></span>  
 <span data-ttu-id="04315-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="04315-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="04315-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="04315-113">Child Elements</span></span>  
  
|<span data-ttu-id="04315-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="04315-114">Element</span></span>|<span data-ttu-id="04315-115">Popis</span><span class="sxs-lookup"><span data-stu-id="04315-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="04315-116">Obsahuje seznam tříd šifrování, které mají mapování na popisného názvu do  **\<nameEntry >** element.</span><span class="sxs-lookup"><span data-stu-id="04315-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="04315-117">Mapuje název třídy algoritmus popisný název, který umožňuje jednu třídu k mít mnoho popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="04315-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04315-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="04315-118">Parent Elements</span></span>  
  
|<span data-ttu-id="04315-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="04315-119">Element</span></span>|<span data-ttu-id="04315-120">Popis</span><span class="sxs-lookup"><span data-stu-id="04315-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="04315-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04315-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="04315-122">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="04315-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="04315-123">Obsahuje mapování třídy popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="04315-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="04315-124">Obsahuje \<cryptographySettings – > elementu.</span><span class="sxs-lookup"><span data-stu-id="04315-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="04315-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="04315-125">Example</span></span>  
 <span data-ttu-id="04315-126">Následující příklad ukazuje, jak používat  **\<cryptoNameMapping >** element tak, aby odkazovaly kryptografické třídy a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="04315-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="04315-127">Řetězec "RSA" můžete poté předat do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použít <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metoda vrátí `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="04315-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="04315-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="04315-128">See Also</span></span>  
 [<span data-ttu-id="04315-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="04315-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="04315-130">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="04315-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="04315-131">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="04315-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="04315-132">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="04315-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
