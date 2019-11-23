---
title: <mscorlib> – element pro nastavení šifrování
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 4e2159cda5f35b5795804dede09ec17d07d71b23
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699734"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="aea70-102">\<element > mscorlib pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="aea70-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="aea70-103">Obsahuje [prvek\<cryptographySettings >](cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="aea70-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[<span data-ttu-id="aea70-104">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="aea70-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="aea70-105">&nbsp;&nbsp; **\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="aea70-105">&nbsp;&nbsp;**\<mscorlib>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea70-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aea70-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aea70-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aea70-107">Attributes and Elements</span></span>  
 <span data-ttu-id="aea70-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aea70-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aea70-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="aea70-109">Attributes</span></span>  
 <span data-ttu-id="aea70-110">Žádné.</span><span class="sxs-lookup"><span data-stu-id="aea70-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aea70-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aea70-111">Child Elements</span></span>  
  
|<span data-ttu-id="aea70-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="aea70-112">Element</span></span>|<span data-ttu-id="aea70-113">Popis</span><span class="sxs-lookup"><span data-stu-id="aea70-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="aea70-114">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="aea70-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aea70-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aea70-115">Parent Elements</span></span>  
  
|<span data-ttu-id="aea70-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="aea70-116">Element</span></span>|<span data-ttu-id="aea70-117">Popis</span><span class="sxs-lookup"><span data-stu-id="aea70-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="aea70-118">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aea70-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aea70-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="aea70-119">Example</span></span>  
 <span data-ttu-id="aea70-120">Následující příklad ukazuje způsob použití prvku **\<mscorlib >** k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="aea70-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="aea70-121">Pak můžete předat řetězec "RSA" do metody <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> a použít metodu <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> k vrácení objektu `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="aea70-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aea70-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aea70-122">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="aea70-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="aea70-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="aea70-124">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="aea70-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="aea70-125">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="aea70-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="aea70-126">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="aea70-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
