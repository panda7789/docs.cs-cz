---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 1d367d0c5d14e6e75539dd2b20cdffcf2b34963d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962783"
---
# <a name="securitybindingelement"></a><span data-ttu-id="ea0c4-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ea0c4-102">SecurityBindingElement</span></span>
<span data-ttu-id="ea0c4-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ea0c4-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea0c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea0c4-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="ea0c4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ea0c4-105">Methods</span></span>  
 <span data-ttu-id="ea0c4-106">Třída SecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="ea0c4-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ea0c4-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ea0c4-107">Properties</span></span>  
 <span data-ttu-id="ea0c4-108">Třída SecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ea0c4-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="ea0c4-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ea0c4-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="ea0c4-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ea0c4-110">Data type: string</span></span>  
  
 <span data-ttu-id="ea0c4-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ea0c4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea0c4-112">Určuje algoritmy, které mají být použity s vazbou.</span><span class="sxs-lookup"><span data-stu-id="ea0c4-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="ea0c4-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="ea0c4-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="ea0c4-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="ea0c4-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="ea0c4-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ea0c4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea0c4-116">Logická hodnota určující, zda každá zpráva obsahuje časovou známku.</span><span class="sxs-lookup"><span data-stu-id="ea0c4-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="ea0c4-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="ea0c4-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="ea0c4-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ea0c4-118">Data type: string</span></span>  
  
 <span data-ttu-id="ea0c4-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ea0c4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea0c4-120">Zdroj šifry použitý k vytvoření klíče.</span><span class="sxs-lookup"><span data-stu-id="ea0c4-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="ea0c4-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ea0c4-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="ea0c4-122">Datový typ: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ea0c4-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="ea0c4-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ea0c4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea0c4-124">Specifické vlastnosti zabezpečení vazby pro lokální službu.</span><span class="sxs-lookup"><span data-stu-id="ea0c4-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="ea0c4-125">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="ea0c4-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="ea0c4-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ea0c4-126">Data type: string</span></span>  
  
 <span data-ttu-id="ea0c4-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ea0c4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea0c4-128">Verze použitá pro zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="ea0c4-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="ea0c4-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="ea0c4-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="ea0c4-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ea0c4-130">Data type: string</span></span>  
  
 <span data-ttu-id="ea0c4-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ea0c4-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea0c4-132">Pořadí prvků v záhlaví zabezpečení pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="ea0c4-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea0c4-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea0c4-133">Requirements</span></span>  
  
|<span data-ttu-id="ea0c4-134">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="ea0c4-134">MOF</span></span>|<span data-ttu-id="ea0c4-135">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ea0c4-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ea0c4-136">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ea0c4-136">Namespace</span></span>|<span data-ttu-id="ea0c4-137">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ea0c4-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea0c4-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea0c4-138">See also</span></span>

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
