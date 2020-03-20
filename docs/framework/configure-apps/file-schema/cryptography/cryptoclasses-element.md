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
ms.openlocfilehash: c93fadf51297d59ab499e25de283700364903049
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155243"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="bf89f-102">\<kryptotřídy> element</span><span class="sxs-lookup"><span data-stu-id="bf89f-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="bf89f-103">Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v [ \<elementu nameEntry>.](nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf89f-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="bf89f-104">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="bf89f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="bf89f-105">&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="bf89f-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="bf89f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kryptografieNastavení>**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf89f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="bf89f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<kryptonamemapping>**](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf89f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="bf89f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<kryptotřídy>**</span><span class="sxs-lookup"><span data-stu-id="bf89f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf89f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf89f-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf89f-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bf89f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bf89f-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bf89f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf89f-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="bf89f-112">Attributes</span></span>  
 <span data-ttu-id="bf89f-113">Žádné.</span><span class="sxs-lookup"><span data-stu-id="bf89f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf89f-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bf89f-114">Child Elements</span></span>  
  
|<span data-ttu-id="bf89f-115">Element</span><span class="sxs-lookup"><span data-stu-id="bf89f-115">Element</span></span>|<span data-ttu-id="bf89f-116">Popis</span><span class="sxs-lookup"><span data-stu-id="bf89f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf89f-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="bf89f-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="bf89f-118">Obsahuje kryptografickou třídu, která má mapování na popisný název v \*\* \<elementu nameEntry>.\*\*</span><span class="sxs-lookup"><span data-stu-id="bf89f-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf89f-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bf89f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bf89f-120">Element</span><span class="sxs-lookup"><span data-stu-id="bf89f-120">Element</span></span>|<span data-ttu-id="bf89f-121">Popis</span><span class="sxs-lookup"><span data-stu-id="bf89f-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bf89f-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf89f-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="bf89f-123">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="bf89f-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="bf89f-124">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="bf89f-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="bf89f-125">Obsahuje `cryptographySettings` prvek.</span><span class="sxs-lookup"><span data-stu-id="bf89f-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bf89f-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf89f-126">Example</span></span>  
 <span data-ttu-id="bf89f-127">Následující příklad ukazuje, jak použít \*\* \<prvek cryptoClass>\*\* k odkazování na kryptografickou třídu a ke konfiguraci runtime.</span><span class="sxs-lookup"><span data-stu-id="bf89f-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="bf89f-128">Potom můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> a použít `MyCryptoRSAClass` metodu k vrácení objektu.</span><span class="sxs-lookup"><span data-stu-id="bf89f-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf89f-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf89f-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="bf89f-130">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="bf89f-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bf89f-131">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="bf89f-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bf89f-132">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="bf89f-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="bf89f-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="bf89f-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="bf89f-134">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="bf89f-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
