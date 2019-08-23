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
ms.openlocfilehash: 6a868f62c6a327012a6225b86bf0103d178d6ab7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921174"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="b3c7e-102">\<cryptoClass – element ></span><span class="sxs-lookup"><span data-stu-id="b3c7e-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="b3c7e-103">Obsahuje třídu kryptografie, která má mapování na popisný název v [ \<elementu nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b3c7e-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="b3c7e-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b3c7e-104">\<configuration></span></span>  
<span data-ttu-id="b3c7e-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="b3c7e-105">\<mscorlib></span></span>  
<span data-ttu-id="b3c7e-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="b3c7e-106">\<cryptographySettings></span></span>  
<span data-ttu-id="b3c7e-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="b3c7e-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="b3c7e-108">\<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="b3c7e-108">\<cryptoClasses></span></span>  
<span data-ttu-id="b3c7e-109">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="b3c7e-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c7e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3c7e-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3c7e-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b3c7e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b3c7e-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b3c7e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3c7e-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="b3c7e-113">Attributes</span></span>  
  
|<span data-ttu-id="b3c7e-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="b3c7e-114">Attribute</span></span>|<span data-ttu-id="b3c7e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b3c7e-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="b3c7e-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b3c7e-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="b3c7e-117">Obsahuje informace pro třídu kryptografie.</span><span class="sxs-lookup"><span data-stu-id="b3c7e-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="b3c7e-118">Tento atribut slouží k zadání krátkého názvu vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="b3c7e-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="b3c7e-119">Je nutné zadat řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="b3c7e-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3c7e-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b3c7e-120">Child Elements</span></span>  
 <span data-ttu-id="b3c7e-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="b3c7e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3c7e-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b3c7e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b3c7e-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="b3c7e-123">Element</span></span>|<span data-ttu-id="b3c7e-124">Popis</span><span class="sxs-lookup"><span data-stu-id="b3c7e-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b3c7e-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b3c7e-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="b3c7e-126">Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v [ \<elementu nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b3c7e-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="b3c7e-127">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="b3c7e-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="b3c7e-128">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="b3c7e-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="b3c7e-129">Obsahuje element cryptographySettings >. [ \<](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="b3c7e-129">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b3c7e-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3c7e-130">Example</span></span>  
 <span data-ttu-id="b3c7e-131">Následující příklad ukazuje použití  **\<prvku cryptoClass >** pro odkazování na třídu kryptografie a konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b3c7e-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="b3c7e-132">Pak můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě a <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> použít metodu k vrácení `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="b3c7e-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3c7e-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3c7e-133">See also</span></span>

- [<span data-ttu-id="b3c7e-134">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b3c7e-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b3c7e-135">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="b3c7e-135">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b3c7e-136">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="b3c7e-136">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="b3c7e-137">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="b3c7e-137">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
