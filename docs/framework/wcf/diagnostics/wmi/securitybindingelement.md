---
title: SecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5de844bc2741768e1b3c53278f20ad4900ffaac1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="securitybindingelement"></a><span data-ttu-id="be28d-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="be28d-102">SecurityBindingElement</span></span>
<span data-ttu-id="be28d-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="be28d-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be28d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be28d-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="be28d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="be28d-105">Methods</span></span>  
 <span data-ttu-id="be28d-106">Třída elementu SecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="be28d-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="be28d-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="be28d-107">Properties</span></span>  
 <span data-ttu-id="be28d-108">Třída elementu SecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="be28d-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="be28d-109">defaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="be28d-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="be28d-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="be28d-110">Data type: string</span></span>  
  
 <span data-ttu-id="be28d-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be28d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be28d-112">Určuje algoritmy pro použití s vazby.</span><span class="sxs-lookup"><span data-stu-id="be28d-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="be28d-113">includeTimestamp</span><span class="sxs-lookup"><span data-stu-id="be28d-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="be28d-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="be28d-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="be28d-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be28d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be28d-116">Logická hodnota, která určuje, zda každá zpráva obsahuje časové razítko.</span><span class="sxs-lookup"><span data-stu-id="be28d-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="be28d-117">keyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="be28d-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="be28d-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="be28d-118">Data type: string</span></span>  
  
 <span data-ttu-id="be28d-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be28d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be28d-120">Zdroj šifry použitý k vytvoření klíče.</span><span class="sxs-lookup"><span data-stu-id="be28d-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="be28d-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="be28d-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="be28d-122">Datový typ: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="be28d-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="be28d-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be28d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be28d-124">Vlastnosti konkrétní bezpečnostní vazby pro místní služby.</span><span class="sxs-lookup"><span data-stu-id="be28d-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="be28d-125">messageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="be28d-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="be28d-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="be28d-126">Data type: string</span></span>  
  
 <span data-ttu-id="be28d-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be28d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be28d-128">Je verze použitá pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="be28d-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="be28d-129">securityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="be28d-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="be28d-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="be28d-130">Data type: string</span></span>  
  
 <span data-ttu-id="be28d-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be28d-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be28d-132">Pořadí prvků v záhlaví zabezpečení pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="be28d-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be28d-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be28d-133">Requirements</span></span>  
  
|<span data-ttu-id="be28d-134">MOF</span><span class="sxs-lookup"><span data-stu-id="be28d-134">MOF</span></span>|<span data-ttu-id="be28d-135">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="be28d-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="be28d-136">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="be28d-136">Namespace</span></span>|<span data-ttu-id="be28d-137">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="be28d-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be28d-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="be28d-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
