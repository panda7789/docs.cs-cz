---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 706cec5c414197ebabda7939728b95be32582e0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770747"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="b0541-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b0541-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="b0541-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b0541-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0541-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0541-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b0541-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b0541-105">Methods</span></span>  
 <span data-ttu-id="b0541-106">Třída prvkem MsmqTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="b0541-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b0541-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b0541-107">Properties</span></span>  
 <span data-ttu-id="b0541-108">Třída prvkem MsmqTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b0541-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="b0541-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="b0541-109">MaxPoolSize</span></span>  
 <span data-ttu-id="b0541-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="b0541-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="b0541-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b0541-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0541-112">Maximální velikost fondu, který obsahuje objekty interní MSMQ zprávy.</span><span class="sxs-lookup"><span data-stu-id="b0541-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="b0541-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="b0541-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="b0541-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b0541-114">Data type: string</span></span>  
  
 <span data-ttu-id="b0541-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b0541-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0541-116">Hodnota výčtu, která označuje přenos zařazených do fronty komunikačního kanálu, který tato vazba používá.</span><span class="sxs-lookup"><span data-stu-id="b0541-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="b0541-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="b0541-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="b0541-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="b0541-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="b0541-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b0541-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0541-120">Vrátí logickou hodnotu, která určuje, zda mají být adresy fronty převedeny pomocí služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b0541-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0541-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0541-121">Requirements</span></span>  
  
|<span data-ttu-id="b0541-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="b0541-122">MOF</span></span>|<span data-ttu-id="b0541-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b0541-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b0541-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b0541-124">Namespace</span></span>|<span data-ttu-id="b0541-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b0541-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0541-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0541-126">See also</span></span>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
