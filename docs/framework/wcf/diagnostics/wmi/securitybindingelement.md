---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 1d367d0c5d14e6e75539dd2b20cdffcf2b34963d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153852"
---
# <a name="securitybindingelement"></a><span data-ttu-id="6b704-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="6b704-102">SecurityBindingElement</span></span>
<span data-ttu-id="6b704-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="6b704-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b704-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b704-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="6b704-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6b704-105">Methods</span></span>  
 <span data-ttu-id="6b704-106">Třída SecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="6b704-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6b704-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6b704-107">Properties</span></span>  
 <span data-ttu-id="6b704-108">Třída SecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="6b704-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="6b704-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="6b704-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="6b704-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="6b704-110">Data type: string</span></span>  
  
 <span data-ttu-id="6b704-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6b704-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6b704-112">Určuje algoritmy, které mají být použity s vazbou.</span><span class="sxs-lookup"><span data-stu-id="6b704-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="6b704-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="6b704-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="6b704-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="6b704-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="6b704-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6b704-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6b704-116">Logická hodnota určující, zda každá zpráva obsahuje časovou známku.</span><span class="sxs-lookup"><span data-stu-id="6b704-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="6b704-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="6b704-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="6b704-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="6b704-118">Data type: string</span></span>  
  
 <span data-ttu-id="6b704-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6b704-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6b704-120">Zdroj šifry použitý k vytvoření klíče.</span><span class="sxs-lookup"><span data-stu-id="6b704-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="6b704-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="6b704-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="6b704-122">Datový typ: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="6b704-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="6b704-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6b704-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6b704-124">Specifické vlastnosti zabezpečení vazby pro lokální službu.</span><span class="sxs-lookup"><span data-stu-id="6b704-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="6b704-125">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="6b704-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="6b704-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="6b704-126">Data type: string</span></span>  
  
 <span data-ttu-id="6b704-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6b704-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6b704-128">Verze použitá pro zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="6b704-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="6b704-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="6b704-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="6b704-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="6b704-130">Data type: string</span></span>  
  
 <span data-ttu-id="6b704-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6b704-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6b704-132">Pořadí prvků v záhlaví zabezpečení pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="6b704-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b704-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b704-133">Requirements</span></span>  
  
|<span data-ttu-id="6b704-134">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="6b704-134">MOF</span></span>|<span data-ttu-id="6b704-135">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6b704-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6b704-136">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="6b704-136">Namespace</span></span>|<span data-ttu-id="6b704-137">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6b704-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b704-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b704-138">See also</span></span>

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
