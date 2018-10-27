---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 79d8b1f4a5127ca36eb57954cff6ee6a97e55e41
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182655"
---
# <a name="transportbindingelement"></a><span data-ttu-id="9f848-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9f848-102">TransportBindingElement</span></span>
<span data-ttu-id="9f848-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9f848-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f848-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f848-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9f848-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9f848-105">Methods</span></span>  
 <span data-ttu-id="9f848-106">Třída TransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="9f848-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9f848-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9f848-107">Properties</span></span>  
 <span data-ttu-id="9f848-108">Třída TransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="9f848-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="9f848-109">Vlastnost manualAddressing</span><span class="sxs-lookup"><span data-stu-id="9f848-109">ManualAddressing</span></span>  
 <span data-ttu-id="9f848-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="9f848-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="9f848-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9f848-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f848-112">Logická hodnota určující, zda chce uživatel převzít kontrolu nad adresováním zpráv.</span><span class="sxs-lookup"><span data-stu-id="9f848-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="9f848-113">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="9f848-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="9f848-114">Datový typ: sint64</span><span class="sxs-lookup"><span data-stu-id="9f848-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="9f848-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9f848-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f848-116">Maximální velikost vyrovnávací paměti fondu pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="9f848-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="9f848-117">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="9f848-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="9f848-118">Datový typ: sint64</span><span class="sxs-lookup"><span data-stu-id="9f848-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="9f848-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9f848-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f848-120">Maximální velikost zprávy zpracované touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="9f848-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="9f848-121">Schéma</span><span class="sxs-lookup"><span data-stu-id="9f848-121">Scheme</span></span>  
 <span data-ttu-id="9f848-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="9f848-122">Data type: string</span></span>  
  
 <span data-ttu-id="9f848-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9f848-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f848-124">Schéma identifikátoru URI pro přenos.</span><span class="sxs-lookup"><span data-stu-id="9f848-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f848-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f848-125">Requirements</span></span>  
  
|<span data-ttu-id="9f848-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="9f848-126">MOF</span></span>|<span data-ttu-id="9f848-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9f848-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9f848-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="9f848-128">Namespace</span></span>|<span data-ttu-id="9f848-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9f848-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f848-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f848-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
