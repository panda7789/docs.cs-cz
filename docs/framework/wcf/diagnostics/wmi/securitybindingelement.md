---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
author: BrucePerlerMS
ms.openlocfilehash: 19c65b3028ad63b8a78205d00f44cc32322648d5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47396845"
---
# <a name="securitybindingelement"></a><span data-ttu-id="e7d24-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e7d24-102">SecurityBindingElement</span></span>
<span data-ttu-id="e7d24-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e7d24-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7d24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7d24-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="e7d24-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e7d24-105">Methods</span></span>  
 <span data-ttu-id="e7d24-106">Třída SecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e7d24-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e7d24-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e7d24-107">Properties</span></span>  
 <span data-ttu-id="e7d24-108">Třída SecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e7d24-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="e7d24-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="e7d24-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="e7d24-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e7d24-110">Data type: string</span></span>  
  
 <span data-ttu-id="e7d24-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e7d24-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7d24-112">Určuje algoritmy, které mají být použity s vazbou.</span><span class="sxs-lookup"><span data-stu-id="e7d24-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="e7d24-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="e7d24-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="e7d24-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="e7d24-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="e7d24-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e7d24-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7d24-116">Logická hodnota určující, zda každá zpráva obsahuje časovou známku.</span><span class="sxs-lookup"><span data-stu-id="e7d24-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="e7d24-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="e7d24-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="e7d24-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e7d24-118">Data type: string</span></span>  
  
 <span data-ttu-id="e7d24-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e7d24-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7d24-120">Zdroj šifry použitý k vytvoření klíče.</span><span class="sxs-lookup"><span data-stu-id="e7d24-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="e7d24-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e7d24-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="e7d24-122">Datový typ: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e7d24-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="e7d24-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e7d24-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7d24-124">Specifické vlastnosti zabezpečení vazby pro lokální službu.</span><span class="sxs-lookup"><span data-stu-id="e7d24-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="e7d24-125">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="e7d24-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="e7d24-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e7d24-126">Data type: string</span></span>  
  
 <span data-ttu-id="e7d24-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e7d24-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7d24-128">Verze použitá pro zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="e7d24-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="e7d24-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="e7d24-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="e7d24-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e7d24-130">Data type: string</span></span>  
  
 <span data-ttu-id="e7d24-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e7d24-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7d24-132">Pořadí prvků v záhlaví zabezpečení pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="e7d24-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7d24-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7d24-133">Requirements</span></span>  
  
|<span data-ttu-id="e7d24-134">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="e7d24-134">MOF</span></span>|<span data-ttu-id="e7d24-135">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e7d24-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e7d24-136">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e7d24-136">Namespace</span></span>|<span data-ttu-id="e7d24-137">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e7d24-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7d24-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7d24-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
