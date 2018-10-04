---
title: '&lt;certificateValidator&gt;'
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 65b8aa6fa4422579ce0d1c5e33d3418ea051612a
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48776880"
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="df78b-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="df78b-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="df78b-103">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="df78b-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="df78b-104">Tento typ se používá jenom v případě, `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) prvek je nastaven na "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="df78b-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="df78b-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="df78b-105">\<system.identityModel></span></span>  
<span data-ttu-id="df78b-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="df78b-106">\<identityConfiguration></span></span>  
<span data-ttu-id="df78b-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="df78b-107">\<certificateValidation></span></span>  
<span data-ttu-id="df78b-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="df78b-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df78b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df78b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df78b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="df78b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="df78b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="df78b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df78b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="df78b-112">Attributes</span></span>  
  
|<span data-ttu-id="df78b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="df78b-113">Attribute</span></span>|<span data-ttu-id="df78b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="df78b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df78b-115">– typ</span><span class="sxs-lookup"><span data-stu-id="df78b-115">type</span></span>|<span data-ttu-id="df78b-116">Určuje, která je odvozena z vlastního typu <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="df78b-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="df78b-117">Nastavte `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) prvku "Vlastní" a pomocí tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="df78b-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="df78b-118">Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="df78b-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="df78b-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="df78b-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df78b-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="df78b-120">Child Elements</span></span>  
 <span data-ttu-id="df78b-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="df78b-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df78b-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="df78b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="df78b-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="df78b-123">Element</span></span>|<span data-ttu-id="df78b-124">Popis</span><span class="sxs-lookup"><span data-stu-id="df78b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df78b-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="df78b-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="df78b-126">Určuje nastavení, které obslužné rutiny tokenů používat ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="df78b-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="df78b-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="df78b-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
