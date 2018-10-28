---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 92aca4c790607de91314aacf6414d0dfacea9a9f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193159"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="566f2-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="566f2-102">PeerSecuritySettings</span></span>
<span data-ttu-id="566f2-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="566f2-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="566f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="566f2-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="566f2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="566f2-105">Methods</span></span>  
 <span data-ttu-id="566f2-106">Třída PeerSecuritySettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="566f2-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="566f2-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="566f2-107">Properties</span></span>  
 <span data-ttu-id="566f2-108">Třída PeerSecuritySettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="566f2-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="566f2-109">Režim</span><span class="sxs-lookup"><span data-stu-id="566f2-109">Mode</span></span>  
 <span data-ttu-id="566f2-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="566f2-110">Data type: string</span></span>  
  
 <span data-ttu-id="566f2-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="566f2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="566f2-112">Určuje, zda zpráva úrovni a koncovým bodem nakonfigurovaným s vazbou používají zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="566f2-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="566f2-113">Přenos</span><span class="sxs-lookup"><span data-stu-id="566f2-113">Transport</span></span>  
 <span data-ttu-id="566f2-114">Datový typ: třída PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="566f2-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="566f2-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="566f2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="566f2-116">Nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="566f2-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="566f2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="566f2-117">Requirements</span></span>  
  
|<span data-ttu-id="566f2-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="566f2-118">MOF</span></span>|<span data-ttu-id="566f2-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="566f2-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="566f2-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="566f2-120">Namespace</span></span>|<span data-ttu-id="566f2-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="566f2-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="566f2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="566f2-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
