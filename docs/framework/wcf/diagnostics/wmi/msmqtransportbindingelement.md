---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 33cd9c427ed5ad04eaf9e9889f60f091f335d1e7
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50045985"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="d74b6-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d74b6-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="d74b6-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d74b6-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d74b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d74b6-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d74b6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d74b6-105">Methods</span></span>  
 <span data-ttu-id="d74b6-106">Třída prvkem MsmqTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d74b6-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d74b6-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d74b6-107">Properties</span></span>  
 <span data-ttu-id="d74b6-108">Třída prvkem MsmqTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d74b6-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="d74b6-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="d74b6-109">MaxPoolSize</span></span>  
 <span data-ttu-id="d74b6-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d74b6-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="d74b6-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d74b6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d74b6-112">Maximální velikost fondu, který obsahuje objekty interní MSMQ zprávy.</span><span class="sxs-lookup"><span data-stu-id="d74b6-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="d74b6-113">Třída queueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="d74b6-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="d74b6-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d74b6-114">Data type: string</span></span>  
  
 <span data-ttu-id="d74b6-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d74b6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d74b6-116">Hodnota výčtu, která označuje přenos zařazených do fronty komunikačního kanálu, který tato vazba používá.</span><span class="sxs-lookup"><span data-stu-id="d74b6-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="d74b6-117">Třída UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="d74b6-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="d74b6-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="d74b6-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d74b6-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d74b6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d74b6-120">Vrátí logickou hodnotu, která určuje, zda mají být adresy fronty převedeny pomocí služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d74b6-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d74b6-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d74b6-121">Requirements</span></span>  
  
|<span data-ttu-id="d74b6-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="d74b6-122">MOF</span></span>|<span data-ttu-id="d74b6-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d74b6-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d74b6-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d74b6-124">Namespace</span></span>|<span data-ttu-id="d74b6-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d74b6-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d74b6-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="d74b6-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
