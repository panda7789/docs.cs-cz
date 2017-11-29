---
title: '&lt;certificateValidator&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 74dd0827ee073d57c82729ec1e6a9a672aa1f404
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="346ec-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="346ec-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="346ec-103">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="346ec-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="346ec-104">Tento typ se používá pouze v případě `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element je nastaven na hodnotu "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="346ec-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="346ec-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="346ec-105">\<system.identityModel></span></span>  
<span data-ttu-id="346ec-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="346ec-106">\<identityConfiguration></span></span>  
<span data-ttu-id="346ec-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="346ec-107">\<certificateValidation></span></span>  
<span data-ttu-id="346ec-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="346ec-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="346ec-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="346ec-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="346ec-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="346ec-110">Attributes and Elements</span></span>  
 <span data-ttu-id="346ec-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="346ec-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="346ec-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="346ec-112">Attributes</span></span>  
  
|<span data-ttu-id="346ec-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="346ec-113">Attribute</span></span>|<span data-ttu-id="346ec-114">Popis</span><span class="sxs-lookup"><span data-stu-id="346ec-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="346ec-115">– typ</span><span class="sxs-lookup"><span data-stu-id="346ec-115">type</span></span>|<span data-ttu-id="346ec-116">Určuje vlastního typu, který je odvozen od <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="346ec-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="346ec-117">Nastavte `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element "Vlastní" pomocí tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="346ec-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="346ec-118">Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na typ vlastní](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="346ec-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="346ec-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="346ec-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="346ec-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="346ec-120">Child Elements</span></span>  
 <span data-ttu-id="346ec-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="346ec-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="346ec-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="346ec-122">Parent Elements</span></span>  
  
|<span data-ttu-id="346ec-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="346ec-123">Element</span></span>|<span data-ttu-id="346ec-124">Popis</span><span class="sxs-lookup"><span data-stu-id="346ec-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="346ec-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="346ec-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="346ec-126">Určuje nastavení, které tokenu obslužné rutiny používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="346ec-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="346ec-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="346ec-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
