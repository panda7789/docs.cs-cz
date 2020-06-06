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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088550"
---
# <a name="oidentry-element"></a><span data-ttu-id="c61bd-102">Element \<oidEntry></span><span class="sxs-lookup"><span data-stu-id="c61bd-102">\<oidEntry> Element</span></span>
<span data-ttu-id="c61bd-103">Mapuje identifikátor objektu ASN. 1 (OID) na popisný název.</span><span class="sxs-lookup"><span data-stu-id="c61bd-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a><span data-ttu-id="c61bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c61bd-104">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c61bd-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c61bd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c61bd-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c61bd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c61bd-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="c61bd-107">Attributes</span></span>  
  
|<span data-ttu-id="c61bd-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="c61bd-108">Attribute</span></span>|<span data-ttu-id="c61bd-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c61bd-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c61bd-110">**IDENTIFIKÁTOR**</span><span class="sxs-lookup"><span data-stu-id="c61bd-110">**OID**</span></span>|<span data-ttu-id="c61bd-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c61bd-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="c61bd-112">Určuje ID ASN. 1, které odpovídá algoritmu implementovanému vaší třídou.</span><span class="sxs-lookup"><span data-stu-id="c61bd-112">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="c61bd-113">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="c61bd-113">**name**</span></span>|<span data-ttu-id="c61bd-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c61bd-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="c61bd-115">Určuje hodnotu atributu **Name** ve [\<nameEntry>](nameentry-element.md) značce.</span><span class="sxs-lookup"><span data-stu-id="c61bd-115">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c61bd-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c61bd-116">Child Elements</span></span>  
 <span data-ttu-id="c61bd-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="c61bd-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c61bd-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c61bd-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c61bd-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="c61bd-119">Element</span></span>|<span data-ttu-id="c61bd-120">Description</span><span class="sxs-lookup"><span data-stu-id="c61bd-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c61bd-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c61bd-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="c61bd-122">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="c61bd-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="c61bd-123">Obsahuje `cryptographySettings` element.</span><span class="sxs-lookup"><span data-stu-id="c61bd-123">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="c61bd-124">Obsahuje mapování identifikátoru objektu ASN. 1 na třídy.</span><span class="sxs-lookup"><span data-stu-id="c61bd-124">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c61bd-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c61bd-125">Remarks</span></span>  
 <span data-ttu-id="c61bd-126">Identifikátory objektů ASN. 1 identifikují algoritmy v některých kryptografických formátech.</span><span class="sxs-lookup"><span data-stu-id="c61bd-126">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="c61bd-127">Namapujte identifikátory objektů na popisné názvy algoritmů, které chcete identifikovat.</span><span class="sxs-lookup"><span data-stu-id="c61bd-127">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c61bd-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="c61bd-128">Example</span></span>  
 <span data-ttu-id="c61bd-129">Následující příklad ukazuje, jak použít **\<oidEntry>** element k mapování identifikátoru objektu pro algoritmus hash RIPEMD-160 na implementaci tohoto algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="c61bd-129">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c61bd-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="c61bd-130">See also</span></span>

- [<span data-ttu-id="c61bd-131">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c61bd-131">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c61bd-132">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="c61bd-132">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c61bd-133">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="c61bd-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="c61bd-134">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="c61bd-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="c61bd-135">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="c61bd-135">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
