---
title: Element <cryptoClass>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: db3681ea141bb7e3905f6a470f5c74ce05f6ef4b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699790"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="b40b4-102">@no__t – element > 0cryptoClass</span><span class="sxs-lookup"><span data-stu-id="b40b4-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="b40b4-103">Obsahuje třídu kryptografie, která má mapování na popisný název v prvku [\<nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b40b4-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="b40b4-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="b40b4-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b40b4-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b40b4-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="b40b4-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="b40b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="b40b4-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="b40b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="b40b4-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="b40b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>  
<span data-ttu-id="b40b4-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1cryptoClass >**</span><span class="sxs-lookup"><span data-stu-id="b40b4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b40b4-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b40b4-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b40b4-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b40b4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b40b4-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b40b4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b40b4-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="b40b4-113">Attributes</span></span>  
  
|<span data-ttu-id="b40b4-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="b40b4-114">Attribute</span></span>|<span data-ttu-id="b40b4-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b40b4-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="b40b4-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b40b4-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="b40b4-117">Obsahuje informace pro třídu kryptografie.</span><span class="sxs-lookup"><span data-stu-id="b40b4-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="b40b4-118">Tento atribut slouží k zadání krátkého názvu vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="b40b4-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="b40b4-119">Je nutné zadat řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="b40b4-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b40b4-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b40b4-120">Child Elements</span></span>  
 <span data-ttu-id="b40b4-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="b40b4-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b40b4-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b40b4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b40b4-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="b40b4-123">Element</span></span>|<span data-ttu-id="b40b4-124">Popis</span><span class="sxs-lookup"><span data-stu-id="b40b4-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b40b4-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b40b4-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="b40b4-126">Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v prvku [\<nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b40b4-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="b40b4-127">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="b40b4-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="b40b4-128">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="b40b4-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="b40b4-129">Obsahuje prvek [> \<cryptographySettings](cryptographysettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b40b4-129">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b40b4-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="b40b4-130">Example</span></span>  
 <span data-ttu-id="b40b4-131">Následující příklad ukazuje, jak použít prvek **> \<cryptoClass** k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b40b4-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="b40b4-132">Pak můžete předat řetězec "RSA" metodě <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> a použít metodu <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pro vrácení objektu `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="b40b4-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b40b4-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b40b4-133">See also</span></span>

- [<span data-ttu-id="b40b4-134">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b40b4-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b40b4-135">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="b40b4-135">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b40b4-136">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="b40b4-136">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="b40b4-137">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="b40b4-137">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
