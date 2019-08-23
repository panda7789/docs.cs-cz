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
ms.openlocfilehash: c780087246ea91846896037a245b82493251e538
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921065"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="68684-102">\<Element > mscorlib pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="68684-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="68684-103">Obsahuje element cryptographySettings >. [ \<](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="68684-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="68684-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="68684-104">\<configuration></span></span>  
<span data-ttu-id="68684-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="68684-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68684-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68684-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68684-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="68684-107">Attributes and Elements</span></span>  
 <span data-ttu-id="68684-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="68684-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68684-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="68684-109">Attributes</span></span>  
 <span data-ttu-id="68684-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="68684-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="68684-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="68684-111">Child Elements</span></span>  
  
|<span data-ttu-id="68684-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="68684-112">Element</span></span>|<span data-ttu-id="68684-113">Popis</span><span class="sxs-lookup"><span data-stu-id="68684-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="68684-114">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="68684-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68684-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="68684-115">Parent Elements</span></span>  
  
|<span data-ttu-id="68684-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="68684-116">Element</span></span>|<span data-ttu-id="68684-117">Popis</span><span class="sxs-lookup"><span data-stu-id="68684-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="68684-118">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="68684-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="68684-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="68684-119">Example</span></span>  
 <span data-ttu-id="68684-120">Následující příklad ukazuje způsob použití  **\<prvku > mscorlib** k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="68684-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="68684-121">Pak můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě a <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> použít metodu k vrácení `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="68684-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="68684-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68684-122">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="68684-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="68684-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="68684-124">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="68684-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="68684-125">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="68684-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="68684-126">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="68684-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
