---
title: Element <oidMap>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: a28eaf68fe1e6ab3f26592eee5ae2d0f2e7a3256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155164"
---
# <a name="oidmap-element"></a><span data-ttu-id="191b5-102">\<Map> prvek</span><span class="sxs-lookup"><span data-stu-id="191b5-102">\<oidMap> Element</span></span>
<span data-ttu-id="191b5-103">Obsahuje mapování identifikátorů objektu ASN.1 (OID) na třídy.</span><span class="sxs-lookup"><span data-stu-id="191b5-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

<span data-ttu-id="191b5-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="191b5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="191b5-105">&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="191b5-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="191b5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kryptografieNastavení>**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="191b5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="191b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="191b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**</span></span>

## <a name="syntax"></a><span data-ttu-id="191b5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="191b5-108">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="191b5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="191b5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="191b5-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="191b5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="191b5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="191b5-111">Attributes</span></span>  
 <span data-ttu-id="191b5-112">Žádné.</span><span class="sxs-lookup"><span data-stu-id="191b5-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="191b5-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="191b5-113">Child Elements</span></span>  
  
|<span data-ttu-id="191b5-114">Element</span><span class="sxs-lookup"><span data-stu-id="191b5-114">Element</span></span>|<span data-ttu-id="191b5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="191b5-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="191b5-116">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="191b5-116">\<oidEntry></span></span>](oidentry-element.md)|<span data-ttu-id="191b5-117">Mapuje OID ASN.1 na popisný název.</span><span class="sxs-lookup"><span data-stu-id="191b5-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="191b5-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="191b5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="191b5-119">Element</span><span class="sxs-lookup"><span data-stu-id="191b5-119">Element</span></span>|<span data-ttu-id="191b5-120">Popis</span><span class="sxs-lookup"><span data-stu-id="191b5-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="191b5-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="191b5-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="191b5-122">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="191b5-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="191b5-123">Obsahuje `cryptographySettings` prvek.</span><span class="sxs-lookup"><span data-stu-id="191b5-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="191b5-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="191b5-124">Example</span></span>  
 <span data-ttu-id="191b5-125">Následující příklad ukazuje, jak použít \*\* \<oidMap>\*\* prvek obsahovat mapování OID pro algoritmus hash RIPEMD-160 na implementaci tohoto algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="191b5-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="191b5-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="191b5-126">See also</span></span>

- [<span data-ttu-id="191b5-127">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="191b5-127">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="191b5-128">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="191b5-128">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="191b5-129">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="191b5-129">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="191b5-130">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="191b5-130">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="191b5-131">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="191b5-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
