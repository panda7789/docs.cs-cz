---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: bdb5ca7400a41dd724c2ad7fc76695a82874ded6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112369"
---
# <a name="transportbindingelement"></a><span data-ttu-id="7eb1a-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="7eb1a-102">TransportBindingElement</span></span>
<span data-ttu-id="7eb1a-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="7eb1a-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eb1a-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7eb1a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7eb1a-105">Methods</span></span>  
 <span data-ttu-id="7eb1a-106">Třída TransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="7eb1a-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7eb1a-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7eb1a-107">Properties</span></span>  
 <span data-ttu-id="7eb1a-108">Třída TransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7eb1a-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="7eb1a-109">Vlastnost manualAddressing</span><span class="sxs-lookup"><span data-stu-id="7eb1a-109">ManualAddressing</span></span>  
 <span data-ttu-id="7eb1a-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="7eb1a-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="7eb1a-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7eb1a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7eb1a-112">Logická hodnota určující, zda chce uživatel převzít kontrolu nad adresováním zpráv.</span><span class="sxs-lookup"><span data-stu-id="7eb1a-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="7eb1a-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="7eb1a-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="7eb1a-114">Datový typ: sint64</span><span class="sxs-lookup"><span data-stu-id="7eb1a-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="7eb1a-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7eb1a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7eb1a-116">Maximální velikost vyrovnávací paměti fondu pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7eb1a-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="7eb1a-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="7eb1a-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="7eb1a-118">Datový typ: sint64</span><span class="sxs-lookup"><span data-stu-id="7eb1a-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="7eb1a-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7eb1a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7eb1a-120">Maximální velikost zprávy zpracované touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="7eb1a-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="7eb1a-121">Schéma</span><span class="sxs-lookup"><span data-stu-id="7eb1a-121">Scheme</span></span>  
 <span data-ttu-id="7eb1a-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7eb1a-122">Data type: string</span></span>  
  
 <span data-ttu-id="7eb1a-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7eb1a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7eb1a-124">Schéma identifikátoru URI pro přenos.</span><span class="sxs-lookup"><span data-stu-id="7eb1a-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eb1a-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7eb1a-125">Requirements</span></span>  
  
|<span data-ttu-id="7eb1a-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="7eb1a-126">MOF</span></span>|<span data-ttu-id="7eb1a-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7eb1a-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7eb1a-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7eb1a-128">Namespace</span></span>|<span data-ttu-id="7eb1a-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7eb1a-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7eb1a-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7eb1a-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TransportBindingElement>
