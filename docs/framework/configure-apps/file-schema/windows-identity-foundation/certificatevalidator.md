---
title: '&lt;certificateValidator&gt;'
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 65b8aa6fa4422579ce0d1c5e33d3418ea051612a
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48849695"
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="ebfc4-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="ebfc4-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="ebfc4-103">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="ebfc4-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="ebfc4-104">Tento typ se používá jenom v případě, `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) prvek je nastaven na "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="ebfc4-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="ebfc4-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ebfc4-105">\<system.identityModel></span></span>  
<span data-ttu-id="ebfc4-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ebfc4-106">\<identityConfiguration></span></span>  
<span data-ttu-id="ebfc4-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="ebfc4-107">\<certificateValidation></span></span>  
<span data-ttu-id="ebfc4-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="ebfc4-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebfc4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebfc4-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebfc4-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ebfc4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ebfc4-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ebfc4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebfc4-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="ebfc4-112">Attributes</span></span>  
  
|<span data-ttu-id="ebfc4-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="ebfc4-113">Attribute</span></span>|<span data-ttu-id="ebfc4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ebfc4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ebfc4-115">– typ</span><span class="sxs-lookup"><span data-stu-id="ebfc4-115">type</span></span>|<span data-ttu-id="ebfc4-116">Určuje, která je odvozena z vlastního typu <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="ebfc4-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="ebfc4-117">Nastavte `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) prvku "Vlastní" a pomocí tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="ebfc4-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="ebfc4-118">Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="ebfc4-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="ebfc4-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ebfc4-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebfc4-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ebfc4-120">Child Elements</span></span>  
 <span data-ttu-id="ebfc4-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="ebfc4-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebfc4-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ebfc4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ebfc4-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="ebfc4-123">Element</span></span>|<span data-ttu-id="ebfc4-124">Popis</span><span class="sxs-lookup"><span data-stu-id="ebfc4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ebfc4-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="ebfc4-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="ebfc4-126">Určuje nastavení, které obslužné rutiny tokenů používat ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="ebfc4-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ebfc4-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebfc4-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
