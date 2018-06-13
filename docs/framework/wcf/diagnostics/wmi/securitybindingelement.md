---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ceb674ea7c20386acb821d3a41c1ad0c743a7607
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487552"
---
# <a name="securitybindingelement"></a><span data-ttu-id="ab0d9-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ab0d9-102">SecurityBindingElement</span></span>
<span data-ttu-id="ab0d9-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ab0d9-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab0d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab0d9-104">Syntax</span></span>  
  
```  
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ab0d9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ab0d9-105">Methods</span></span>  
 <span data-ttu-id="ab0d9-106">Třída elementu SecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="ab0d9-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ab0d9-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ab0d9-107">Properties</span></span>  
 <span data-ttu-id="ab0d9-108">Třída elementu SecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ab0d9-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="ab0d9-109">defaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ab0d9-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="ab0d9-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ab0d9-110">Data type: string</span></span>  
  
 <span data-ttu-id="ab0d9-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ab0d9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab0d9-112">Určuje algoritmy pro použití s vazby.</span><span class="sxs-lookup"><span data-stu-id="ab0d9-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="ab0d9-113">includeTimestamp</span><span class="sxs-lookup"><span data-stu-id="ab0d9-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="ab0d9-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="ab0d9-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="ab0d9-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ab0d9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab0d9-116">Logická hodnota, která určuje, zda každá zpráva obsahuje časové razítko.</span><span class="sxs-lookup"><span data-stu-id="ab0d9-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="ab0d9-117">keyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="ab0d9-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="ab0d9-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ab0d9-118">Data type: string</span></span>  
  
 <span data-ttu-id="ab0d9-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ab0d9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab0d9-120">Zdroj šifry použitý k vytvoření klíče.</span><span class="sxs-lookup"><span data-stu-id="ab0d9-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="ab0d9-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ab0d9-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="ab0d9-122">Datový typ: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ab0d9-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="ab0d9-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ab0d9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab0d9-124">Vlastnosti konkrétní bezpečnostní vazby pro místní služby.</span><span class="sxs-lookup"><span data-stu-id="ab0d9-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="ab0d9-125">messageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="ab0d9-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="ab0d9-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ab0d9-126">Data type: string</span></span>  
  
 <span data-ttu-id="ab0d9-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ab0d9-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab0d9-128">Je verze použitá pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="ab0d9-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="ab0d9-129">securityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="ab0d9-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="ab0d9-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ab0d9-130">Data type: string</span></span>  
  
 <span data-ttu-id="ab0d9-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ab0d9-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab0d9-132">Pořadí prvků v záhlaví zabezpečení pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="ab0d9-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab0d9-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab0d9-133">Requirements</span></span>  
  
|<span data-ttu-id="ab0d9-134">MOF</span><span class="sxs-lookup"><span data-stu-id="ab0d9-134">MOF</span></span>|<span data-ttu-id="ab0d9-135">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ab0d9-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ab0d9-136">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ab0d9-136">Namespace</span></span>|<span data-ttu-id="ab0d9-137">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ab0d9-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab0d9-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab0d9-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
