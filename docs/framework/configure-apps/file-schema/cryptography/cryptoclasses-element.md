---
title: Element <cryptoClasses>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 6601417f0b80f623b7698c4b072c35eca44343b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732886"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="68657-102">\<element > cryptoClasses</span><span class="sxs-lookup"><span data-stu-id="68657-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="68657-103">Obsahuje seznam tříd kryptografie, které mají mapování na popisný název v prvku [\<nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="68657-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="68657-104">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="68657-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="68657-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="68657-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="68657-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="68657-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="68657-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="68657-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="68657-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptoClasses >**</span><span class="sxs-lookup"><span data-stu-id="68657-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68657-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68657-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68657-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="68657-110">Attributes and Elements</span></span>  
 <span data-ttu-id="68657-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="68657-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68657-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="68657-112">Attributes</span></span>  
 <span data-ttu-id="68657-113">Žádné.</span><span class="sxs-lookup"><span data-stu-id="68657-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="68657-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="68657-114">Child Elements</span></span>  
  
|<span data-ttu-id="68657-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="68657-115">Element</span></span>|<span data-ttu-id="68657-116">Popis</span><span class="sxs-lookup"><span data-stu-id="68657-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68657-117">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="68657-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="68657-118">Obsahuje třídu kryptografie, která má mapování na popisný název v prvku **\<nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="68657-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68657-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="68657-119">Parent Elements</span></span>  
  
|<span data-ttu-id="68657-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="68657-120">Element</span></span>|<span data-ttu-id="68657-121">Popis</span><span class="sxs-lookup"><span data-stu-id="68657-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="68657-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="68657-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="68657-123">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="68657-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="68657-124">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="68657-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="68657-125">Obsahuje element `cryptographySettings`.</span><span class="sxs-lookup"><span data-stu-id="68657-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="68657-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="68657-126">Example</span></span>  
 <span data-ttu-id="68657-127">Následující příklad ukazuje, jak použít **\<cryptoClass >** elementu k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="68657-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="68657-128">Pak můžete předat řetězec "RSA" do metody <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> a použít metodu <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> k vrácení objektu `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="68657-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="68657-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="68657-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="68657-130">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="68657-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="68657-131">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="68657-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="68657-132">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="68657-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="68657-133">System. Security. Cryptography. objektu CryptoConfig. CreateFromName</span><span class="sxs-lookup"><span data-stu-id="68657-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="68657-134">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="68657-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
