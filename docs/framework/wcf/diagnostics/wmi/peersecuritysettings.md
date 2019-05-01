---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 1c33e1ce710fea3b1698a6dab47a199e40388f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963004"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="2ebd3-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2ebd3-102">PeerSecuritySettings</span></span>
<span data-ttu-id="2ebd3-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2ebd3-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ebd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ebd3-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2ebd3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2ebd3-105">Methods</span></span>  
 <span data-ttu-id="2ebd3-106">Třída PeerSecuritySettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="2ebd3-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2ebd3-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2ebd3-107">Properties</span></span>  
 <span data-ttu-id="2ebd3-108">Třída PeerSecuritySettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2ebd3-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="2ebd3-109">Režim</span><span class="sxs-lookup"><span data-stu-id="2ebd3-109">Mode</span></span>  
 <span data-ttu-id="2ebd3-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2ebd3-110">Data type: string</span></span>  
  
 <span data-ttu-id="2ebd3-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2ebd3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2ebd3-112">Určuje, zda zpráva úrovni a koncovým bodem nakonfigurovaným s vazbou používají zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="2ebd3-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="2ebd3-113">Přenos</span><span class="sxs-lookup"><span data-stu-id="2ebd3-113">Transport</span></span>  
 <span data-ttu-id="2ebd3-114">Datový typ: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2ebd3-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="2ebd3-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2ebd3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2ebd3-116">Nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="2ebd3-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ebd3-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ebd3-117">Requirements</span></span>  
  
|<span data-ttu-id="2ebd3-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="2ebd3-118">MOF</span></span>|<span data-ttu-id="2ebd3-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2ebd3-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2ebd3-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="2ebd3-120">Namespace</span></span>|<span data-ttu-id="2ebd3-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2ebd3-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ebd3-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ebd3-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
