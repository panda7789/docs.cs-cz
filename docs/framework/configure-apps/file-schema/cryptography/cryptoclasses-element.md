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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155243"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="fc2f4-102">Element \<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="fc2f4-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="fc2f4-103">Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v [\<nameEntry>](nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="fc2f4-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**  
  
## <a name="syntax"></a><span data-ttu-id="fc2f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc2f4-104">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc2f4-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fc2f4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fc2f4-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fc2f4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc2f4-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="fc2f4-107">Attributes</span></span>  
 <span data-ttu-id="fc2f4-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="fc2f4-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fc2f4-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fc2f4-109">Child Elements</span></span>  
  
|<span data-ttu-id="fc2f4-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="fc2f4-110">Element</span></span>|<span data-ttu-id="fc2f4-111">Description</span><span class="sxs-lookup"><span data-stu-id="fc2f4-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoClass>](cryptoclass-element.md)|<span data-ttu-id="fc2f4-112">Obsahuje třídu kryptografie, která má mapování na popisný název v **\<nameEntry>** elementu.</span><span class="sxs-lookup"><span data-stu-id="fc2f4-112">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc2f4-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fc2f4-113">Parent Elements</span></span>  
  
|<span data-ttu-id="fc2f4-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="fc2f4-114">Element</span></span>|<span data-ttu-id="fc2f4-115">Description</span><span class="sxs-lookup"><span data-stu-id="fc2f4-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fc2f4-116">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc2f4-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="fc2f4-117">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="fc2f4-117">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="fc2f4-118">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="fc2f4-118">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="fc2f4-119">Obsahuje `cryptographySettings` element.</span><span class="sxs-lookup"><span data-stu-id="fc2f4-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fc2f4-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc2f4-120">Example</span></span>  
 <span data-ttu-id="fc2f4-121">Následující příklad ukazuje, jak použít **\<cryptoClass>** element k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="fc2f4-121">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="fc2f4-122">Pak můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě a použít <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu k vrácení `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="fc2f4-122">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fc2f4-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc2f4-123">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="fc2f4-124">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="fc2f4-124">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fc2f4-125">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="fc2f4-125">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fc2f4-126">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="fc2f4-126">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="fc2f4-127">System. Security. Cryptography. objektu CryptoConfig. CreateFromName</span><span class="sxs-lookup"><span data-stu-id="fc2f4-127">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="fc2f4-128">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="fc2f4-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
