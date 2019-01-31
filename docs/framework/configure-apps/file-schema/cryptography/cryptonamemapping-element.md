---
title: Element <cryptoNameMapping>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: ff3300f57fd4681875e2791610cc5a0d0dcba31b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281473"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="a992e-102">\<cryptoNameMapping> Element</span><span class="sxs-lookup"><span data-stu-id="a992e-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="a992e-103">Obsahuje mapování tříd pro popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="a992e-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="a992e-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a992e-104">\<configuration></span></span>  
<span data-ttu-id="a992e-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="a992e-105">\<mscorlib></span></span>  
<span data-ttu-id="a992e-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="a992e-106">\<cryptographySettings></span></span>  
<span data-ttu-id="a992e-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="a992e-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a992e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a992e-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a992e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a992e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a992e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a992e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a992e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a992e-111">Attributes</span></span>  
 <span data-ttu-id="a992e-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="a992e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a992e-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a992e-113">Child Elements</span></span>  
  
|<span data-ttu-id="a992e-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="a992e-114">Element</span></span>|<span data-ttu-id="a992e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a992e-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="a992e-116">Obsahuje seznam šifrovacích tříd, které mají na popisný název v mapování  **\<nameEntry >** elementu.</span><span class="sxs-lookup"><span data-stu-id="a992e-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="a992e-117">Název třídy mapuje na algoritmus popisný název, který umožňuje jedna třída má mnoho popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="a992e-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a992e-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a992e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a992e-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="a992e-119">Element</span></span>|<span data-ttu-id="a992e-120">Popis</span><span class="sxs-lookup"><span data-stu-id="a992e-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a992e-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a992e-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="a992e-122">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="a992e-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="a992e-123">Obsahuje mapování tříd pro popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="a992e-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="a992e-124">Obsahuje \<cryptographySettings – > element.</span><span class="sxs-lookup"><span data-stu-id="a992e-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a992e-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="a992e-125">Example</span></span>  
 <span data-ttu-id="a992e-126">Následující příklad ukazuje způsob použití  **\<cryptoNameMapping >** element tak, aby odkazovaly kryptografickou třídu a konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a992e-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="a992e-127">Můžete poté předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použití <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu pro návrat `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="a992e-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a992e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a992e-128">See also</span></span>
- [<span data-ttu-id="a992e-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a992e-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="a992e-130">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="a992e-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="a992e-131">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="a992e-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="a992e-132">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="a992e-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
