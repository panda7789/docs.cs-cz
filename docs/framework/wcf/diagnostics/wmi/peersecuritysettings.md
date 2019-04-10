---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 1c33e1ce710fea3b1698a6dab47a199e40388f5a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217884"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="4ec13-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4ec13-102">PeerSecuritySettings</span></span>
<span data-ttu-id="4ec13-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4ec13-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ec13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ec13-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4ec13-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4ec13-105">Methods</span></span>  
 <span data-ttu-id="4ec13-106">Třída PeerSecuritySettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="4ec13-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4ec13-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4ec13-107">Properties</span></span>  
 <span data-ttu-id="4ec13-108">Třída PeerSecuritySettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4ec13-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="4ec13-109">Režim</span><span class="sxs-lookup"><span data-stu-id="4ec13-109">Mode</span></span>  
 <span data-ttu-id="4ec13-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4ec13-110">Data type: string</span></span>  
  
 <span data-ttu-id="4ec13-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4ec13-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4ec13-112">Určuje, zda zpráva úrovni a koncovým bodem nakonfigurovaným s vazbou používají zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="4ec13-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="4ec13-113">Přenos</span><span class="sxs-lookup"><span data-stu-id="4ec13-113">Transport</span></span>  
 <span data-ttu-id="4ec13-114">Datový typ: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4ec13-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="4ec13-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4ec13-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4ec13-116">Nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="4ec13-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ec13-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ec13-117">Requirements</span></span>  
  
|<span data-ttu-id="4ec13-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="4ec13-118">MOF</span></span>|<span data-ttu-id="4ec13-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4ec13-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4ec13-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="4ec13-120">Namespace</span></span>|<span data-ttu-id="4ec13-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4ec13-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ec13-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ec13-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
