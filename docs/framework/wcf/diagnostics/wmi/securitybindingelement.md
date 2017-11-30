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
ms.openlocfilehash: b567c173c5a04421bce57585d96b8b45144c5625
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="securitybindingelement"></a><span data-ttu-id="59e3e-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="59e3e-102">SecurityBindingElement</span></span>
<span data-ttu-id="59e3e-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="59e3e-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59e3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59e3e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="59e3e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="59e3e-105">Methods</span></span>  
 <span data-ttu-id="59e3e-106">Třída elementu SecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="59e3e-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="59e3e-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="59e3e-107">Properties</span></span>  
 <span data-ttu-id="59e3e-108">Třída elementu SecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="59e3e-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="59e3e-109">defaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="59e3e-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="59e3e-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="59e3e-110">Data type: string</span></span>  
  
 <span data-ttu-id="59e3e-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="59e3e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59e3e-112">Určuje algoritmy pro použití s vazby.</span><span class="sxs-lookup"><span data-stu-id="59e3e-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="59e3e-113">includeTimestamp</span><span class="sxs-lookup"><span data-stu-id="59e3e-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="59e3e-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="59e3e-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="59e3e-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="59e3e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59e3e-116">Logická hodnota, která určuje, zda každá zpráva obsahuje časové razítko.</span><span class="sxs-lookup"><span data-stu-id="59e3e-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="59e3e-117">keyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="59e3e-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="59e3e-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="59e3e-118">Data type: string</span></span>  
  
 <span data-ttu-id="59e3e-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="59e3e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59e3e-120">Zdroj šifry použitý k vytvoření klíče.</span><span class="sxs-lookup"><span data-stu-id="59e3e-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="59e3e-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="59e3e-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="59e3e-122">Datový typ: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="59e3e-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="59e3e-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="59e3e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59e3e-124">Vlastnosti konkrétní bezpečnostní vazby pro místní služby.</span><span class="sxs-lookup"><span data-stu-id="59e3e-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="59e3e-125">messageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="59e3e-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="59e3e-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="59e3e-126">Data type: string</span></span>  
  
 <span data-ttu-id="59e3e-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="59e3e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59e3e-128">Je verze použitá pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="59e3e-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="59e3e-129">securityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="59e3e-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="59e3e-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="59e3e-130">Data type: string</span></span>  
  
 <span data-ttu-id="59e3e-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="59e3e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59e3e-132">Pořadí prvků v záhlaví zabezpečení pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="59e3e-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59e3e-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59e3e-133">Requirements</span></span>  
  
|<span data-ttu-id="59e3e-134">MOF</span><span class="sxs-lookup"><span data-stu-id="59e3e-134">MOF</span></span>|<span data-ttu-id="59e3e-135">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="59e3e-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="59e3e-136">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="59e3e-136">Namespace</span></span>|<span data-ttu-id="59e3e-137">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="59e3e-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59e3e-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="59e3e-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
