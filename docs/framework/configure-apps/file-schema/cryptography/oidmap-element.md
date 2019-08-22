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
ms.openlocfilehash: e01cdd942237141b8ef35495d3b74d6b2282a865
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664260"
---
# <a name="oidmap-element"></a><span data-ttu-id="0e63d-102">\<oidMap – element ></span><span class="sxs-lookup"><span data-stu-id="0e63d-102">\<oidMap> Element</span></span>
<span data-ttu-id="0e63d-103">Obsahuje mapování identifikátoru objektu ASN. 1 na třídy.</span><span class="sxs-lookup"><span data-stu-id="0e63d-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="0e63d-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0e63d-104">\<configuration></span></span>  
<span data-ttu-id="0e63d-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="0e63d-105">\<mscorlib></span></span>  
<span data-ttu-id="0e63d-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="0e63d-106">\<cryptographySettings></span></span>  
<span data-ttu-id="0e63d-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="0e63d-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e63d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e63d-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e63d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0e63d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0e63d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0e63d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e63d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="0e63d-111">Attributes</span></span>  
 <span data-ttu-id="0e63d-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="0e63d-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0e63d-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0e63d-113">Child Elements</span></span>  
  
|<span data-ttu-id="0e63d-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e63d-114">Element</span></span>|<span data-ttu-id="0e63d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="0e63d-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e63d-116">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="0e63d-116">\<oidEntry></span></span>](oidentry-element.md)|<span data-ttu-id="0e63d-117">Mapuje identifikátor ID ASN. 1 na popisný název.</span><span class="sxs-lookup"><span data-stu-id="0e63d-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e63d-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0e63d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0e63d-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e63d-119">Element</span></span>|<span data-ttu-id="0e63d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="0e63d-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0e63d-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0e63d-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="0e63d-122">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="0e63d-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="0e63d-123">`cryptographySettings` Obsahuje element.</span><span class="sxs-lookup"><span data-stu-id="0e63d-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0e63d-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e63d-124">Example</span></span>  
 <span data-ttu-id="0e63d-125">Následující příklad ukazuje způsob použití  **\<prvku oidMap >** k zahrnutí mapování OID pro algoritmus hash RIPEMD-160 na implementaci tohoto algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="0e63d-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e63d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e63d-126">See also</span></span>

- [<span data-ttu-id="0e63d-127">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0e63d-127">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0e63d-128">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="0e63d-128">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0e63d-129">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="0e63d-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="0e63d-130">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="0e63d-130">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="0e63d-131">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="0e63d-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
