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
ms.openlocfilehash: 4872fbd6fa043902e8c69f158bee5d0c915ec83a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088663"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="7f68a-102">Element \<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="7f68a-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="7f68a-103">Obsahuje třídu kryptografie, která má mapování na popisný název v [\<nameEntry>](nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7f68a-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**

## <a name="syntax"></a><span data-ttu-id="7f68a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f68a-104">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f68a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7f68a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7f68a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7f68a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f68a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f68a-107">Attributes</span></span>  
  
|<span data-ttu-id="7f68a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="7f68a-108">Attribute</span></span>|<span data-ttu-id="7f68a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7f68a-109">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="7f68a-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f68a-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="7f68a-111">Obsahuje informace pro třídu kryptografie.</span><span class="sxs-lookup"><span data-stu-id="7f68a-111">Contains the information for the cryptography class.</span></span> <span data-ttu-id="7f68a-112">Tento atribut slouží k zadání krátkého názvu vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="7f68a-112">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="7f68a-113">Je nutné zadat řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="7f68a-113">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f68a-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7f68a-114">Child Elements</span></span>  
 <span data-ttu-id="7f68a-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="7f68a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f68a-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7f68a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7f68a-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f68a-117">Element</span></span>|<span data-ttu-id="7f68a-118">Description</span><span class="sxs-lookup"><span data-stu-id="7f68a-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7f68a-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7f68a-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="7f68a-120">Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v [\<nameEntry>](nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7f68a-120">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="7f68a-121">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="7f68a-121">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="7f68a-122">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="7f68a-122">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="7f68a-123">Obsahuje [\<cryptographySettings>](cryptographysettings-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="7f68a-123">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7f68a-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f68a-124">Example</span></span>  
 <span data-ttu-id="7f68a-125">Následující příklad ukazuje, jak použít **\<cryptoClass>** element k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7f68a-125">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="7f68a-126">Pak můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě a použít <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu k vrácení `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="7f68a-126">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f68a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f68a-127">See also</span></span>

- [<span data-ttu-id="7f68a-128">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="7f68a-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7f68a-129">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="7f68a-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7f68a-130">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="7f68a-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="7f68a-131">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="7f68a-131">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
