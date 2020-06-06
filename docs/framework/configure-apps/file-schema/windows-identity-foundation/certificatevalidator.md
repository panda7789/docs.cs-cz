---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152785"
---
# \<certificateValidator>
<span data-ttu-id="d4b5f-101">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d4b5f-101">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="d4b5f-102">Tento typ se používá jenom v případě, že `certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) je atribut elementu nastavený na Custom (vlastní).</span><span class="sxs-lookup"><span data-stu-id="d4b5f-102">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**  
  
## <a name="syntax"></a><span data-ttu-id="d4b5f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4b5f-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4b5f-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d4b5f-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d4b5f-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d4b5f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4b5f-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="d4b5f-106">Attributes</span></span>  
  
|<span data-ttu-id="d4b5f-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="d4b5f-107">Attribute</span></span>|<span data-ttu-id="d4b5f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d4b5f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4b5f-109">typ</span><span class="sxs-lookup"><span data-stu-id="d4b5f-109">type</span></span>|<span data-ttu-id="d4b5f-110">Určuje vlastní typ, který je odvozen od <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="d4b5f-110">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="d4b5f-111">`certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) Pro použití tohoto typu nastavte atribut elementu na "Custom".</span><span class="sxs-lookup"><span data-stu-id="d4b5f-111">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="d4b5f-112">Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="d4b5f-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="d4b5f-113">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="d4b5f-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4b5f-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d4b5f-114">Child Elements</span></span>  
 <span data-ttu-id="d4b5f-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="d4b5f-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4b5f-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d4b5f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d4b5f-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="d4b5f-117">Element</span></span>|<span data-ttu-id="d4b5f-118">Description</span><span class="sxs-lookup"><span data-stu-id="d4b5f-118">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="d4b5f-119">Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="d4b5f-119">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d4b5f-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4b5f-120">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
