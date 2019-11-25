---
title: Element <oidEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 4564cf59e3b6cfbdcd9dca06cd0f966d524834de
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088550"
---
# <a name="oidentry-element"></a><span data-ttu-id="22ce8-102">\<element > oidEntry</span><span class="sxs-lookup"><span data-stu-id="22ce8-102">\<oidEntry> Element</span></span>
<span data-ttu-id="22ce8-103">Mapuje identifikátor objektu ASN. 1 (OID) na popisný název.</span><span class="sxs-lookup"><span data-stu-id="22ce8-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

<span data-ttu-id="22ce8-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="22ce8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22ce8-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="22ce8-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="22ce8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="22ce8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="22ce8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidMap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="22ce8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>\
<span data-ttu-id="22ce8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="22ce8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**</span></span>

## <a name="syntax"></a><span data-ttu-id="22ce8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22ce8-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22ce8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="22ce8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="22ce8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="22ce8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22ce8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="22ce8-112">Attributes</span></span>  
  
|<span data-ttu-id="22ce8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="22ce8-113">Attribute</span></span>|<span data-ttu-id="22ce8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="22ce8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22ce8-115">**IDENTIFIKÁTOR**</span><span class="sxs-lookup"><span data-stu-id="22ce8-115">**OID**</span></span>|<span data-ttu-id="22ce8-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="22ce8-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="22ce8-117">Určuje ID ASN. 1, které odpovídá algoritmu implementovanému vaší třídou.</span><span class="sxs-lookup"><span data-stu-id="22ce8-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="22ce8-118">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="22ce8-118">**name**</span></span>|<span data-ttu-id="22ce8-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="22ce8-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="22ce8-120">Určuje hodnotu atributu **název** ve značce [\<nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="22ce8-120">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22ce8-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="22ce8-121">Child Elements</span></span>  
 <span data-ttu-id="22ce8-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="22ce8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22ce8-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="22ce8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="22ce8-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="22ce8-124">Element</span></span>|<span data-ttu-id="22ce8-125">Popis</span><span class="sxs-lookup"><span data-stu-id="22ce8-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="22ce8-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22ce8-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="22ce8-127">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="22ce8-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="22ce8-128">Obsahuje element `cryptographySettings`.</span><span class="sxs-lookup"><span data-stu-id="22ce8-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="22ce8-129">Obsahuje mapování identifikátoru objektu ASN. 1 na třídy.</span><span class="sxs-lookup"><span data-stu-id="22ce8-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22ce8-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22ce8-130">Remarks</span></span>  
 <span data-ttu-id="22ce8-131">Identifikátory objektů ASN. 1 identifikují algoritmy v některých kryptografických formátech.</span><span class="sxs-lookup"><span data-stu-id="22ce8-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="22ce8-132">Namapujte identifikátory objektů na popisné názvy algoritmů, které chcete identifikovat.</span><span class="sxs-lookup"><span data-stu-id="22ce8-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22ce8-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="22ce8-133">Example</span></span>  
 <span data-ttu-id="22ce8-134">Následující příklad ukazuje způsob použití prvku **\<oidEntry >** k mapování identifikátoru objektu pro algoritmus hash RIPEMD-160 na implementaci tohoto algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="22ce8-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22ce8-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22ce8-135">See also</span></span>

- [<span data-ttu-id="22ce8-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="22ce8-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="22ce8-137">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="22ce8-137">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="22ce8-138">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="22ce8-138">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="22ce8-139">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="22ce8-139">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="22ce8-140">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="22ce8-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
