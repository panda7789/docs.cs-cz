---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 30f81dd5948a7d366c1116cffd347c85a396f5ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252115"
---
# <a name="certificatevalidator"></a><span data-ttu-id="75bed-101">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="75bed-101">\<certificateValidator></span></span>
<span data-ttu-id="75bed-102">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="75bed-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="75bed-103">Tento typ se používá pouze v případě `certificateValidationMode` , že je atribut [ \<prvku certificateValidation >](certificatevalidation.md) nastaven na hodnotu "Custom".</span><span class="sxs-lookup"><span data-stu-id="75bed-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="75bed-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="75bed-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75bed-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="75bed-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="75bed-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="75bed-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="75bed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<certificateValidation >** ](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="75bed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="75bed-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateValidator >**</span><span class="sxs-lookup"><span data-stu-id="75bed-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75bed-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75bed-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75bed-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="75bed-110">Attributes and Elements</span></span>  
 <span data-ttu-id="75bed-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="75bed-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75bed-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="75bed-112">Attributes</span></span>  
  
|<span data-ttu-id="75bed-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="75bed-113">Attribute</span></span>|<span data-ttu-id="75bed-114">Popis</span><span class="sxs-lookup"><span data-stu-id="75bed-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75bed-115">– typ</span><span class="sxs-lookup"><span data-stu-id="75bed-115">type</span></span>|<span data-ttu-id="75bed-116">Určuje vlastní typ, který je odvozen od <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="75bed-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="75bed-117">Pro použití tohoto typu nastavte [ atributcertificateValidation>elementuna"Custom"\<](certificatevalidation.md) `certificateValidationMode` .</span><span class="sxs-lookup"><span data-stu-id="75bed-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="75bed-118">Další informace o tom, jak zadat `type` atribut, naleznete v tématu odkazy na [vlastní typ](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="75bed-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="75bed-119">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="75bed-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75bed-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="75bed-120">Child Elements</span></span>  
 <span data-ttu-id="75bed-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="75bed-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75bed-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="75bed-122">Parent Elements</span></span>  
  
|<span data-ttu-id="75bed-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="75bed-123">Element</span></span>|<span data-ttu-id="75bed-124">Popis</span><span class="sxs-lookup"><span data-stu-id="75bed-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75bed-125">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="75bed-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="75bed-126">Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="75bed-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="75bed-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="75bed-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
