---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
author: BrucePerlerMS
ms.openlocfilehash: 19c65b3028ad63b8a78205d00f44cc32322648d5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47069971"
---
# <a name="securitybindingelement"></a><span data-ttu-id="8cb51-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="8cb51-102">SecurityBindingElement</span></span>
<span data-ttu-id="8cb51-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="8cb51-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cb51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cb51-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="8cb51-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8cb51-105">Methods</span></span>  
 <span data-ttu-id="8cb51-106">Třída SecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="8cb51-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8cb51-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8cb51-107">Properties</span></span>  
 <span data-ttu-id="8cb51-108">Třída SecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="8cb51-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="8cb51-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="8cb51-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="8cb51-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8cb51-110">Data type: string</span></span>  
  
 <span data-ttu-id="8cb51-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cb51-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cb51-112">Určuje algoritmy, které mají být použity s vazbou.</span><span class="sxs-lookup"><span data-stu-id="8cb51-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="8cb51-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="8cb51-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="8cb51-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="8cb51-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="8cb51-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cb51-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cb51-116">Logická hodnota určující, zda každá zpráva obsahuje časovou známku.</span><span class="sxs-lookup"><span data-stu-id="8cb51-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="8cb51-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="8cb51-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="8cb51-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8cb51-118">Data type: string</span></span>  
  
 <span data-ttu-id="8cb51-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cb51-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cb51-120">Zdroj šifry použitý k vytvoření klíče.</span><span class="sxs-lookup"><span data-stu-id="8cb51-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="8cb51-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="8cb51-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="8cb51-122">Datový typ: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="8cb51-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="8cb51-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cb51-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cb51-124">Specifické vlastnosti zabezpečení vazby pro lokální službu.</span><span class="sxs-lookup"><span data-stu-id="8cb51-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="8cb51-125">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="8cb51-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="8cb51-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8cb51-126">Data type: string</span></span>  
  
 <span data-ttu-id="8cb51-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cb51-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cb51-128">Verze použitá pro zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="8cb51-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="8cb51-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="8cb51-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="8cb51-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8cb51-130">Data type: string</span></span>  
  
 <span data-ttu-id="8cb51-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cb51-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cb51-132">Pořadí prvků v záhlaví zabezpečení pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="8cb51-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cb51-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8cb51-133">Requirements</span></span>  
  
|<span data-ttu-id="8cb51-134">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="8cb51-134">MOF</span></span>|<span data-ttu-id="8cb51-135">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8cb51-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8cb51-136">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="8cb51-136">Namespace</span></span>|<span data-ttu-id="8cb51-137">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8cb51-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cb51-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="8cb51-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
