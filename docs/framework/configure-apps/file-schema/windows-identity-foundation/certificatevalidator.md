---
title: '&lt;certificateValidator&gt;'
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a4663b0c3a2a6965a977a1d551c47de7e13d144b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="f205d-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="f205d-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="f205d-103">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="f205d-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="f205d-104">Tento typ se používá pouze v případě `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element je nastaven na hodnotu "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="f205d-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="f205d-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f205d-105">\<system.identityModel></span></span>  
<span data-ttu-id="f205d-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f205d-106">\<identityConfiguration></span></span>  
<span data-ttu-id="f205d-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="f205d-107">\<certificateValidation></span></span>  
<span data-ttu-id="f205d-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="f205d-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f205d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f205d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f205d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f205d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f205d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f205d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f205d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f205d-112">Attributes</span></span>  
  
|<span data-ttu-id="f205d-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f205d-113">Attribute</span></span>|<span data-ttu-id="f205d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f205d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f205d-115">– typ</span><span class="sxs-lookup"><span data-stu-id="f205d-115">type</span></span>|<span data-ttu-id="f205d-116">Určuje vlastního typu, který je odvozen od <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="f205d-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="f205d-117">Nastavte `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element "Vlastní" pomocí tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="f205d-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="f205d-118">Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na typ vlastní](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="f205d-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="f205d-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f205d-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f205d-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f205d-120">Child Elements</span></span>  
 <span data-ttu-id="f205d-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="f205d-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f205d-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f205d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f205d-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="f205d-123">Element</span></span>|<span data-ttu-id="f205d-124">Popis</span><span class="sxs-lookup"><span data-stu-id="f205d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f205d-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="f205d-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="f205d-126">Určuje nastavení, které tokenu obslužné rutiny používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f205d-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f205d-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="f205d-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
