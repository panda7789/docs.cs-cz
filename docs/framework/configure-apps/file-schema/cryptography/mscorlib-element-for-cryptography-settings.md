---
title: "&lt;mscorlib&gt; Element pro nastavení kryptografie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 992e62575dccae3f68df27fb7dd027dceab91ffc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a><span data-ttu-id="37176-102">&lt;mscorlib&gt; Element pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="37176-102">&lt;mscorlib&gt; Element for Cryptography Settings</span></span>
<span data-ttu-id="37176-103">Obsahuje [ \<cryptographySettings – > element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="37176-103">Contains the [\<cryptographySettings> element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="37176-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="37176-104">\<configuration></span></span>  
<span data-ttu-id="37176-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="37176-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37176-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37176-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37176-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="37176-107">Attributes and Elements</span></span>  
 <span data-ttu-id="37176-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="37176-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37176-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="37176-109">Attributes</span></span>  
 <span data-ttu-id="37176-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="37176-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="37176-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="37176-111">Child Elements</span></span>  
  
|<span data-ttu-id="37176-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="37176-112">Element</span></span>|<span data-ttu-id="37176-113">Popis</span><span class="sxs-lookup"><span data-stu-id="37176-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="37176-114">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="37176-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37176-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="37176-115">Parent Elements</span></span>  
  
|<span data-ttu-id="37176-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="37176-116">Element</span></span>|<span data-ttu-id="37176-117">Popis</span><span class="sxs-lookup"><span data-stu-id="37176-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="37176-118">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37176-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="37176-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="37176-119">Example</span></span>  
 <span data-ttu-id="37176-120">Následující příklad ukazuje, jak používat  **\<mscorlib >** element tak, aby odkazovaly kryptografické třídy a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="37176-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="37176-121">Řetězec "RSA" můžete poté předat do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použít <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metoda vrátí `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="37176-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="37176-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="37176-122">See Also</span></span>  
 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="37176-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="37176-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="37176-124">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="37176-124">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="37176-125">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="37176-125">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="37176-126">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="37176-126">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
