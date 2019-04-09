---
title: <cryptoNameMapping> Prvek
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: bcf7894dba66736fcc1a30af9b5557549ef25e7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092461"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="262fc-102">\<cryptoNameMapping> Element</span><span class="sxs-lookup"><span data-stu-id="262fc-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="262fc-103">Obsahuje mapování tříd pro popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="262fc-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="262fc-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="262fc-104">\<configuration></span></span>  
<span data-ttu-id="262fc-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="262fc-105">\<mscorlib></span></span>  
<span data-ttu-id="262fc-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="262fc-106">\<cryptographySettings></span></span>  
<span data-ttu-id="262fc-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="262fc-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="262fc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="262fc-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="262fc-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="262fc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="262fc-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="262fc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="262fc-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="262fc-111">Attributes</span></span>  
 <span data-ttu-id="262fc-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="262fc-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="262fc-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="262fc-113">Child Elements</span></span>  
  
|<span data-ttu-id="262fc-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="262fc-114">Element</span></span>|<span data-ttu-id="262fc-115">Popis</span><span class="sxs-lookup"><span data-stu-id="262fc-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="262fc-116">Obsahuje seznam šifrovacích tříd, které mají na popisný název v mapování  **\<nameEntry >** elementu.</span><span class="sxs-lookup"><span data-stu-id="262fc-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="262fc-117">Název třídy mapuje na algoritmus popisný název, který umožňuje jedna třída má mnoho popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="262fc-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="262fc-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="262fc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="262fc-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="262fc-119">Element</span></span>|<span data-ttu-id="262fc-120">Popis</span><span class="sxs-lookup"><span data-stu-id="262fc-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="262fc-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="262fc-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="262fc-122">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="262fc-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="262fc-123">Obsahuje mapování tříd pro popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="262fc-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="262fc-124">Obsahuje \<cryptographySettings – > element.</span><span class="sxs-lookup"><span data-stu-id="262fc-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="262fc-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="262fc-125">Example</span></span>  
 <span data-ttu-id="262fc-126">Následující příklad ukazuje způsob použití  **\<cryptoNameMapping >** element tak, aby odkazovaly kryptografickou třídu a konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="262fc-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="262fc-127">Můžete poté předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použití <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu pro návrat `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="262fc-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="262fc-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="262fc-128">See also</span></span>

- [<span data-ttu-id="262fc-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="262fc-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="262fc-130">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="262fc-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="262fc-131">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="262fc-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="262fc-132">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="262fc-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
