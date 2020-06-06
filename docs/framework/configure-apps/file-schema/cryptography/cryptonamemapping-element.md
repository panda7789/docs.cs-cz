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
ms.openlocfilehash: d31c5cd52ffe0e2a6eb5784735e76436d216444b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155216"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="e7511-102">Element \<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="e7511-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="e7511-103">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="e7511-103">Contains mappings of classes to friendly names.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**

## <a name="syntax"></a><span data-ttu-id="e7511-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7511-104">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7511-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e7511-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e7511-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e7511-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7511-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="e7511-107">Attributes</span></span>  
 <span data-ttu-id="e7511-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="e7511-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e7511-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e7511-109">Child Elements</span></span>  
  
|<span data-ttu-id="e7511-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="e7511-110">Element</span></span>|<span data-ttu-id="e7511-111">Description</span><span class="sxs-lookup"><span data-stu-id="e7511-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="e7511-112">Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v **\<nameEntry>** elementu.</span><span class="sxs-lookup"><span data-stu-id="e7511-112">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="e7511-113">Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.</span><span class="sxs-lookup"><span data-stu-id="e7511-113">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7511-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e7511-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e7511-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="e7511-115">Element</span></span>|<span data-ttu-id="e7511-116">Description</span><span class="sxs-lookup"><span data-stu-id="e7511-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e7511-117">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7511-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="e7511-118">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="e7511-118">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="e7511-119">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="e7511-119">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="e7511-120">Obsahuje \<cryptographySettings> element.</span><span class="sxs-lookup"><span data-stu-id="e7511-120">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e7511-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7511-121">Example</span></span>  
 <span data-ttu-id="e7511-122">Následující příklad ukazuje, jak použít **\<cryptoNameMapping>** element k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e7511-122">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="e7511-123">Pak můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě a použít <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu k vrácení `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="e7511-123">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7511-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7511-124">See also</span></span>

- [<span data-ttu-id="e7511-125">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="e7511-125">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e7511-126">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="e7511-126">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e7511-127">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="e7511-127">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="e7511-128">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="e7511-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
