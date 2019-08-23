---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: c25f183679f41f51ffee4f482bfe7a64763647d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941906"
---
# <a name="certificatevalidator"></a><span data-ttu-id="8cfc2-101">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="8cfc2-101">\<certificateValidator></span></span>
<span data-ttu-id="8cfc2-102">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="8cfc2-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="8cfc2-103">Tento typ se používá pouze v případě `certificateValidationMode` , že je atribut [ \<prvku certificateValidation >](certificatevalidation.md) nastaven na hodnotu "Custom".</span><span class="sxs-lookup"><span data-stu-id="8cfc2-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="8cfc2-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8cfc2-104">\<system.identityModel></span></span>  
<span data-ttu-id="8cfc2-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8cfc2-105">\<identityConfiguration></span></span>  
<span data-ttu-id="8cfc2-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="8cfc2-106">\<certificateValidation></span></span>  
<span data-ttu-id="8cfc2-107">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="8cfc2-107">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cfc2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cfc2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cfc2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8cfc2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8cfc2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8cfc2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cfc2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="8cfc2-111">Attributes</span></span>  
  
|<span data-ttu-id="8cfc2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="8cfc2-112">Attribute</span></span>|<span data-ttu-id="8cfc2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8cfc2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8cfc2-114">– typ</span><span class="sxs-lookup"><span data-stu-id="8cfc2-114">type</span></span>|<span data-ttu-id="8cfc2-115">Určuje vlastní typ, který je odvozen od <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="8cfc2-115">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="8cfc2-116">Pro použití tohoto typu nastavte [ atributcertificateValidation>elementuna"Custom"\<](certificatevalidation.md) `certificateValidationMode` .</span><span class="sxs-lookup"><span data-stu-id="8cfc2-116">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="8cfc2-117">Další informace o tom, jak zadat `type` atribut, naleznete v tématu odkazy na [vlastní typ](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="8cfc2-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="8cfc2-118">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="8cfc2-118">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8cfc2-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8cfc2-119">Child Elements</span></span>  
 <span data-ttu-id="8cfc2-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="8cfc2-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cfc2-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8cfc2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8cfc2-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="8cfc2-122">Element</span></span>|<span data-ttu-id="8cfc2-123">Popis</span><span class="sxs-lookup"><span data-stu-id="8cfc2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cfc2-124">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="8cfc2-124">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="8cfc2-125">Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8cfc2-125">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8cfc2-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="8cfc2-126">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
