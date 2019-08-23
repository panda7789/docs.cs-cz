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
ms.openlocfilehash: cbdf6150010ca2dace3f0610d9caa90c2bf52746
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921047"
---
# <a name="oidentry-element"></a><span data-ttu-id="c76f4-102">\<oidEntry – element ></span><span class="sxs-lookup"><span data-stu-id="c76f4-102">\<oidEntry> Element</span></span>
<span data-ttu-id="c76f4-103">Mapuje identifikátor objektu ASN. 1 (OID) na popisný název.</span><span class="sxs-lookup"><span data-stu-id="c76f4-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="c76f4-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c76f4-104">\<configuration></span></span>  
<span data-ttu-id="c76f4-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="c76f4-105">\<mscorlib></span></span>  
<span data-ttu-id="c76f4-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="c76f4-106">\<cryptographySettings></span></span>  
<span data-ttu-id="c76f4-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="c76f4-107">\<oidMap></span></span>  
<span data-ttu-id="c76f4-108">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="c76f4-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c76f4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c76f4-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c76f4-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c76f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c76f4-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c76f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c76f4-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c76f4-112">Attributes</span></span>  
  
|<span data-ttu-id="c76f4-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c76f4-113">Attribute</span></span>|<span data-ttu-id="c76f4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c76f4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c76f4-115">**IDENTIFIKÁTOR**</span><span class="sxs-lookup"><span data-stu-id="c76f4-115">**OID**</span></span>|<span data-ttu-id="c76f4-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c76f4-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="c76f4-117">Určuje ID ASN. 1, které odpovídá algoritmu implementovanému vaší třídou.</span><span class="sxs-lookup"><span data-stu-id="c76f4-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="c76f4-118">**name**</span><span class="sxs-lookup"><span data-stu-id="c76f4-118">**name**</span></span>|<span data-ttu-id="c76f4-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c76f4-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="c76f4-120">Určuje hodnotu atributu **Name** ve [ \<značce nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="c76f4-120">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c76f4-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c76f4-121">Child Elements</span></span>  
 <span data-ttu-id="c76f4-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="c76f4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c76f4-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c76f4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c76f4-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="c76f4-124">Element</span></span>|<span data-ttu-id="c76f4-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c76f4-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c76f4-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c76f4-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="c76f4-127">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="c76f4-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="c76f4-128">`cryptographySettings` Obsahuje element.</span><span class="sxs-lookup"><span data-stu-id="c76f4-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="c76f4-129">Obsahuje mapování identifikátoru objektu ASN. 1 na třídy.</span><span class="sxs-lookup"><span data-stu-id="c76f4-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c76f4-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c76f4-130">Remarks</span></span>  
 <span data-ttu-id="c76f4-131">Identifikátory objektů ASN. 1 identifikují algoritmy v některých kryptografických formátech.</span><span class="sxs-lookup"><span data-stu-id="c76f4-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="c76f4-132">Namapujte identifikátory objektů na popisné názvy algoritmů, které chcete identifikovat.</span><span class="sxs-lookup"><span data-stu-id="c76f4-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c76f4-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="c76f4-133">Example</span></span>  
 <span data-ttu-id="c76f4-134">Následující příklad ukazuje způsob použití  **\<prvku oidEntry >** k mapování identifikátoru objektu pro algoritmus hash RIPEMD-160 na implementaci tohoto algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="c76f4-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c76f4-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c76f4-135">See also</span></span>

- [<span data-ttu-id="c76f4-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c76f4-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c76f4-137">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="c76f4-137">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c76f4-138">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="c76f4-138">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="c76f4-139">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="c76f4-139">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="c76f4-140">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="c76f4-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
