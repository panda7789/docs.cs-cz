---
title: Message. WriteStartHeaders – metoda (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: c826e6a3b976e5705e9815586441e8a25b64f76e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214868"
---
# <a name="messagewritestartheaders-method"></a><span data-ttu-id="8b834-102">Message. WriteStartHeaders – metoda</span><span class="sxs-lookup"><span data-stu-id="8b834-102">Message.WriteStartHeaders Method</span></span>

<span data-ttu-id="8b834-103">Zapíše počáteční hlavičku do souboru XML voláním metody <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b834-103">Writes the start header into an XML file by calling the <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a><span data-ttu-id="8b834-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b834-104">Parameters</span></span>

- <span data-ttu-id="8b834-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="8b834-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="8b834-106">Zapisovač, který se používá k zápisu počáteční hlavičky do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="8b834-106">The writer that is used to write the start header into an XML file.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b834-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b834-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="8b834-108">Metoda `Message.WriteStartHeaders` je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="8b834-108">The `Message.WriteStartHeaders` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="8b834-109">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8b834-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8b834-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b834-110">Requirements</span></span>

<span data-ttu-id="8b834-111">**Obor názvů:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="8b834-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="8b834-112">**Sestavení:** System. ServiceModel. dll</span><span class="sxs-lookup"><span data-stu-id="8b834-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="8b834-113">**Verze .NET Framework:** K dispozici od verze 3,0.</span><span class="sxs-lookup"><span data-stu-id="8b834-113">**.NET Framework versions:** Available since 3.0.</span></span>
