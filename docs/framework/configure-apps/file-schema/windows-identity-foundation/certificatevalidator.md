---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: df52212305e0865b8c03fdd49068cb7c7da4fa38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667363"
---
# <a name="certificatevalidator"></a><span data-ttu-id="515ff-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="515ff-101">\<certificateValidator></span></span>
<span data-ttu-id="515ff-102">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="515ff-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="515ff-103">Tento typ se používá jenom v případě, `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) prvek je nastaven na "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="515ff-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="515ff-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="515ff-104">\<system.identityModel></span></span>  
<span data-ttu-id="515ff-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="515ff-105">\<identityConfiguration></span></span>  
<span data-ttu-id="515ff-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="515ff-106">\<certificateValidation></span></span>  
<span data-ttu-id="515ff-107">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="515ff-107">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="515ff-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="515ff-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="515ff-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="515ff-109">Attributes and Elements</span></span>  
 <span data-ttu-id="515ff-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="515ff-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="515ff-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="515ff-111">Attributes</span></span>  
  
|<span data-ttu-id="515ff-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="515ff-112">Attribute</span></span>|<span data-ttu-id="515ff-113">Popis</span><span class="sxs-lookup"><span data-stu-id="515ff-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="515ff-114"> – typ</span><span class="sxs-lookup"><span data-stu-id="515ff-114">type</span></span>|<span data-ttu-id="515ff-115">Určuje, která je odvozena z vlastního typu <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="515ff-115">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="515ff-116">Nastavte `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) prvku "Vlastní" a pomocí tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="515ff-116">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="515ff-117">Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="515ff-117">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="515ff-118">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="515ff-118">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="515ff-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="515ff-119">Child Elements</span></span>  
 <span data-ttu-id="515ff-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="515ff-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="515ff-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="515ff-121">Parent Elements</span></span>  
  
|<span data-ttu-id="515ff-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="515ff-122">Element</span></span>|<span data-ttu-id="515ff-123">Popis</span><span class="sxs-lookup"><span data-stu-id="515ff-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="515ff-124">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="515ff-124">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="515ff-125">Určuje nastavení, které obslužné rutiny tokenů používat ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="515ff-125">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="515ff-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="515ff-126">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
