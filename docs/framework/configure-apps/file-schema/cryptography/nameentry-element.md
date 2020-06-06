---
title: Element <nameEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: a339638587f8b544bbc1b0073553f6232ce09694
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71699783"
---
# <a name="nameentry-element"></a><span data-ttu-id="11ec9-102">Element \<nameEntry></span><span class="sxs-lookup"><span data-stu-id="11ec9-102">\<nameEntry> Element</span></span>
<span data-ttu-id="11ec9-103">Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.</span><span class="sxs-lookup"><span data-stu-id="11ec9-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**  
  
## <a name="syntax"></a><span data-ttu-id="11ec9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11ec9-104">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11ec9-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11ec9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="11ec9-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11ec9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11ec9-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="11ec9-107">Attributes</span></span>  
  
|<span data-ttu-id="11ec9-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="11ec9-108">Attribute</span></span>|<span data-ttu-id="11ec9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="11ec9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11ec9-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="11ec9-110">**name**</span></span>|<span data-ttu-id="11ec9-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="11ec9-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="11ec9-112">Určuje popisný název algoritmu, který kryptografická třída implementuje.</span><span class="sxs-lookup"><span data-stu-id="11ec9-112">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="11ec9-113">**Deník**</span><span class="sxs-lookup"><span data-stu-id="11ec9-113">**class**</span></span>|<span data-ttu-id="11ec9-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="11ec9-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="11ec9-115">Určuje hodnotu atributu **Name** v [\<cryptoClass>](cryptoclass-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="11ec9-115">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11ec9-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11ec9-116">Child Elements</span></span>  
 <span data-ttu-id="11ec9-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="11ec9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11ec9-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11ec9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="11ec9-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="11ec9-119">Element</span></span>|<span data-ttu-id="11ec9-120">Description</span><span class="sxs-lookup"><span data-stu-id="11ec9-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="11ec9-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11ec9-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="11ec9-122">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="11ec9-122">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11ec9-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11ec9-123">Remarks</span></span>  
 <span data-ttu-id="11ec9-124">Atribut **Name** může být název jedné z abstraktních tříd nalezených v <xref:System.Security.Cryptography> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="11ec9-124">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="11ec9-125">Při volání metody **Create** na abstraktní kryptografické třídě je název abstraktní třídy předán <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="11ec9-125">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="11ec9-126">**CreateFromName** vrací instanci typu, která je označena atributem **Class** .</span><span class="sxs-lookup"><span data-stu-id="11ec9-126">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="11ec9-127">Pokud je atribut **Name** krátkým názvem, jako je například RSA, můžete použít tento název při volání metody **CreateFromName** .</span><span class="sxs-lookup"><span data-stu-id="11ec9-127">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11ec9-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="11ec9-128">Example</span></span>  
 <span data-ttu-id="11ec9-129">Následující příklad ukazuje, jak použít **\<nameEntry>** element k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="11ec9-129">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="11ec9-130">Pak můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě a použít <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu k vrácení `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="11ec9-130">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11ec9-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="11ec9-131">See also</span></span>

- [<span data-ttu-id="11ec9-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="11ec9-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="11ec9-133">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="11ec9-133">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="11ec9-134">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="11ec9-134">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="11ec9-135">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="11ec9-135">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
