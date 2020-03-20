---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152785"
---
# <a name="certificatevalidator"></a><span data-ttu-id="f2ab4-101">\<certifikátValidator></span><span class="sxs-lookup"><span data-stu-id="f2ab4-101">\<certificateValidator></span></span>
<span data-ttu-id="f2ab4-102">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="f2ab4-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="f2ab4-103">Tento typ se používá `certificateValidationMode` pouze v případě, že atribut [ \<certifikátuValidation>](certificatevalidation.md) element je nastaven na "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="f2ab4-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="f2ab4-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2ab4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f2ab4-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="f2ab4-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="f2ab4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f2ab4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="f2ab4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ověření certifikátu**](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="f2ab4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="f2ab4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certifikátValidator>**</span><span class="sxs-lookup"><span data-stu-id="f2ab4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2ab4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2ab4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2ab4-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f2ab4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f2ab4-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f2ab4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2ab4-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f2ab4-112">Attributes</span></span>  
  
|<span data-ttu-id="f2ab4-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f2ab4-113">Attribute</span></span>|<span data-ttu-id="f2ab4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f2ab4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2ab4-115">type</span><span class="sxs-lookup"><span data-stu-id="f2ab4-115">type</span></span>|<span data-ttu-id="f2ab4-116">Určuje vlastní typ, který je <xref:System.IdentityModel.Selectors.X509CertificateValidator> odvozen od třídy.</span><span class="sxs-lookup"><span data-stu-id="f2ab4-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="f2ab4-117">Nastavte `certificateValidationMode` atribut [ \<certifikátuValidation>](certificatevalidation.md) elementu na "Vlastní" pro použití tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="f2ab4-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="f2ab4-118">Další informace o tom, `type` jak zadat atribut, naleznete v [tématu Vlastní odkazy na typ](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2ab4-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="f2ab4-119">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f2ab4-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2ab4-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f2ab4-120">Child Elements</span></span>  
 <span data-ttu-id="f2ab4-121">Žádný</span><span class="sxs-lookup"><span data-stu-id="f2ab4-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2ab4-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f2ab4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f2ab4-123">Element</span><span class="sxs-lookup"><span data-stu-id="f2ab4-123">Element</span></span>|<span data-ttu-id="f2ab4-124">Popis</span><span class="sxs-lookup"><span data-stu-id="f2ab4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2ab4-125">\<>ověření certifikátu</span><span class="sxs-lookup"><span data-stu-id="f2ab4-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="f2ab4-126">Řídí nastavení, která obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f2ab4-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f2ab4-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2ab4-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
