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
ms.openlocfilehash: 87b24595f5013ad3b981256fd97bc758863c600b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921104"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="ff8f3-102">\<cryptoNameMapping – element ></span><span class="sxs-lookup"><span data-stu-id="ff8f3-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="ff8f3-103">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="ff8f3-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ff8f3-104">\<configuration></span></span>  
<span data-ttu-id="ff8f3-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="ff8f3-105">\<mscorlib></span></span>  
<span data-ttu-id="ff8f3-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="ff8f3-106">\<cryptographySettings></span></span>  
<span data-ttu-id="ff8f3-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="ff8f3-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff8f3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff8f3-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff8f3-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ff8f3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ff8f3-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff8f3-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ff8f3-111">Attributes</span></span>  
 <span data-ttu-id="ff8f3-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="ff8f3-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ff8f3-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ff8f3-113">Child Elements</span></span>  
  
|<span data-ttu-id="ff8f3-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="ff8f3-114">Element</span></span>|<span data-ttu-id="ff8f3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="ff8f3-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="ff8f3-116">Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v  **\<elementu nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="ff8f3-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="ff8f3-117">Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff8f3-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ff8f3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ff8f3-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="ff8f3-119">Element</span></span>|<span data-ttu-id="ff8f3-120">Popis</span><span class="sxs-lookup"><span data-stu-id="ff8f3-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ff8f3-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ff8f3-122">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="ff8f3-123">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="ff8f3-124">Obsahuje element \<cryptographySettings >.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ff8f3-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff8f3-125">Example</span></span>  
 <span data-ttu-id="ff8f3-126">Následující příklad ukazuje způsob použití  **\<prvku cryptoNameMapping >** k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ff8f3-127">Pak můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě a <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> použít metodu k vrácení `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff8f3-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff8f3-128">See also</span></span>

- [<span data-ttu-id="ff8f3-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ff8f3-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ff8f3-130">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="ff8f3-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ff8f3-131">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="ff8f3-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ff8f3-132">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="ff8f3-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
