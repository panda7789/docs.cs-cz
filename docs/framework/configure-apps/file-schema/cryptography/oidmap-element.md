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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155164"
---
# <a name="oidmap-element"></a><span data-ttu-id="b277a-102">Element \<oidMap></span><span class="sxs-lookup"><span data-stu-id="b277a-102">\<oidMap> Element</span></span>
<span data-ttu-id="b277a-103">Obsahuje mapování identifikátoru objektu ASN. 1 na třídy.</span><span class="sxs-lookup"><span data-stu-id="b277a-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a><span data-ttu-id="b277a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b277a-104">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b277a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b277a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b277a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b277a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b277a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b277a-107">Attributes</span></span>  
 <span data-ttu-id="b277a-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="b277a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b277a-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b277a-109">Child Elements</span></span>  
  
|<span data-ttu-id="b277a-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="b277a-110">Element</span></span>|<span data-ttu-id="b277a-111">Description</span><span class="sxs-lookup"><span data-stu-id="b277a-111">Description</span></span>|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|<span data-ttu-id="b277a-112">Mapuje identifikátor ID ASN. 1 na popisný název.</span><span class="sxs-lookup"><span data-stu-id="b277a-112">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b277a-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b277a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b277a-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="b277a-114">Element</span></span>|<span data-ttu-id="b277a-115">Description</span><span class="sxs-lookup"><span data-stu-id="b277a-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b277a-116">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b277a-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="b277a-117">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="b277a-117">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="b277a-118">Obsahuje `cryptographySettings` element.</span><span class="sxs-lookup"><span data-stu-id="b277a-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b277a-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="b277a-119">Example</span></span>  
 <span data-ttu-id="b277a-120">Následující příklad ukazuje, jak použít **\<oidMap>** element k zahrnutí mapování OID pro algoritmus hash RIPEMD-160 na implementaci tohoto algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="b277a-120">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b277a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b277a-121">See also</span></span>

- [<span data-ttu-id="b277a-122">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b277a-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b277a-123">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="b277a-123">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b277a-124">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="b277a-124">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="b277a-125">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="b277a-125">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="b277a-126">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="b277a-126">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
