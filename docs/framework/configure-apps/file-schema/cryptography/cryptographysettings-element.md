---
title: Element <cryptographySettings>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: fe6de09213c6f980e8eb205a318aae50033b2a84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155229"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="b52f6-102">\<kryptografieNastavení> element</span><span class="sxs-lookup"><span data-stu-id="b52f6-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="b52f6-103">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="b52f6-103">Contains cryptography settings.</span></span>  

<span data-ttu-id="b52f6-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b52f6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b52f6-105">&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b52f6-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="b52f6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<kryptografieNastavení>**</span><span class="sxs-lookup"><span data-stu-id="b52f6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b52f6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b52f6-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b52f6-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b52f6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b52f6-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b52f6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b52f6-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b52f6-110">Attributes</span></span>  
 <span data-ttu-id="b52f6-111">Žádné.</span><span class="sxs-lookup"><span data-stu-id="b52f6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b52f6-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b52f6-112">Child Elements</span></span>  
  
|<span data-ttu-id="b52f6-113">Element</span><span class="sxs-lookup"><span data-stu-id="b52f6-113">Element</span></span>|<span data-ttu-id="b52f6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b52f6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b52f6-115">\<kryptonamemapping></span><span class="sxs-lookup"><span data-stu-id="b52f6-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="b52f6-116">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="b52f6-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="b52f6-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="b52f6-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="b52f6-118">Obsahuje mapování identifikátorů objektu ASN.1 (OID) na třídy.</span><span class="sxs-lookup"><span data-stu-id="b52f6-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b52f6-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b52f6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b52f6-120">Element</span><span class="sxs-lookup"><span data-stu-id="b52f6-120">Element</span></span>|<span data-ttu-id="b52f6-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b52f6-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b52f6-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b52f6-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="b52f6-123">Obsahuje `cryptographySettings` prvek.</span><span class="sxs-lookup"><span data-stu-id="b52f6-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b52f6-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="b52f6-124">Example</span></span>  
 <span data-ttu-id="b52f6-125">Následující příklad ukazuje, jak použít \*\* \<kryptografiiNastavení>\*\* prvek k zobrazení mapování názvů kryptografie a mapování OID.</span><span class="sxs-lookup"><span data-stu-id="b52f6-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="b52f6-126">Tento příklad konfiguruje <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> runtime tak, aby vrátí `MyHashClass` objekt a `MyCryptoClass` třída mapuje na identifikátor objektu 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="b52f6-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b52f6-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b52f6-127">See also</span></span>

- [<span data-ttu-id="b52f6-128">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b52f6-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b52f6-129">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="b52f6-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b52f6-130">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="b52f6-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
