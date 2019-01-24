---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: f7c4e30b72af36de1d3088e4ca8cd98ced734104
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692321"
---
# <a name="securitybindingelement"></a><span data-ttu-id="ef479-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ef479-102">SecurityBindingElement</span></span>
<span data-ttu-id="ef479-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ef479-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef479-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef479-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="ef479-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ef479-105">Methods</span></span>  
 <span data-ttu-id="ef479-106">Třída SecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="ef479-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ef479-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ef479-107">Properties</span></span>  
 <span data-ttu-id="ef479-108">Třída SecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ef479-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="ef479-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ef479-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="ef479-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ef479-110">Data type: string</span></span>  
  
 <span data-ttu-id="ef479-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ef479-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef479-112">Určuje algoritmy, které mají být použity s vazbou.</span><span class="sxs-lookup"><span data-stu-id="ef479-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="ef479-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="ef479-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="ef479-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="ef479-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef479-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ef479-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef479-116">Logická hodnota určující, zda každá zpráva obsahuje časovou známku.</span><span class="sxs-lookup"><span data-stu-id="ef479-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="ef479-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="ef479-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="ef479-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ef479-118">Data type: string</span></span>  
  
 <span data-ttu-id="ef479-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ef479-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef479-120">Zdroj šifry použitý k vytvoření klíče.</span><span class="sxs-lookup"><span data-stu-id="ef479-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="ef479-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ef479-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="ef479-122">Datový typ: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ef479-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="ef479-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ef479-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef479-124">Specifické vlastnosti zabezpečení vazby pro lokální službu.</span><span class="sxs-lookup"><span data-stu-id="ef479-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="ef479-125">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="ef479-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="ef479-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ef479-126">Data type: string</span></span>  
  
 <span data-ttu-id="ef479-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ef479-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef479-128">Verze použitá pro zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="ef479-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="ef479-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="ef479-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="ef479-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ef479-130">Data type: string</span></span>  
  
 <span data-ttu-id="ef479-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ef479-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef479-132">Pořadí prvků v záhlaví zabezpečení pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="ef479-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef479-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef479-133">Requirements</span></span>  
  
|<span data-ttu-id="ef479-134">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="ef479-134">MOF</span></span>|<span data-ttu-id="ef479-135">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ef479-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ef479-136">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ef479-136">Namespace</span></span>|<span data-ttu-id="ef479-137">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ef479-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef479-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef479-138">See also</span></span>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
