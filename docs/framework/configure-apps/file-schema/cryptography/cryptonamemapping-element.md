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
ms.openlocfilehash: 45d2da22a7c3486d4c7a638e92d1f3fce6f9883c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699720"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="c56c8-102">@no__t – element > 0cryptoNameMapping</span><span class="sxs-lookup"><span data-stu-id="c56c8-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="c56c8-103">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="c56c8-103">Contains mappings of classes to friendly names.</span></span>  
  
[<span data-ttu-id="c56c8-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="c56c8-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c56c8-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c56c8-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="c56c8-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="c56c8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="c56c8-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="c56c8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c56c8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c56c8-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c56c8-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c56c8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c56c8-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c56c8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c56c8-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c56c8-111">Attributes</span></span>  
 <span data-ttu-id="c56c8-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="c56c8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c56c8-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c56c8-113">Child Elements</span></span>  
  
|<span data-ttu-id="c56c8-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="c56c8-114">Element</span></span>|<span data-ttu-id="c56c8-115">Popis</span><span class="sxs-lookup"><span data-stu-id="c56c8-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="c56c8-116">Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v prvku **\<nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="c56c8-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="c56c8-117">Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.</span><span class="sxs-lookup"><span data-stu-id="c56c8-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c56c8-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c56c8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c56c8-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="c56c8-119">Element</span></span>|<span data-ttu-id="c56c8-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c56c8-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c56c8-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c56c8-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="c56c8-122">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="c56c8-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="c56c8-123">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="c56c8-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="c56c8-124">Obsahuje prvek > \<cryptographySettings.</span><span class="sxs-lookup"><span data-stu-id="c56c8-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c56c8-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="c56c8-125">Example</span></span>  
 <span data-ttu-id="c56c8-126">Následující příklad ukazuje způsob použití prvku **> @no__t 1cryptoNameMapping** k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c56c8-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="c56c8-127">Pak můžete předat řetězec "RSA" metodě <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> a použít metodu <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pro vrácení objektu `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="c56c8-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c56c8-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c56c8-128">See also</span></span>

- [<span data-ttu-id="c56c8-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c56c8-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c56c8-130">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="c56c8-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c56c8-131">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="c56c8-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="c56c8-132">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="c56c8-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
