---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 14150a992130e9ed4734c950d4ed92f1bbd3206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485554"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="2806d-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="2806d-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="2806d-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="2806d-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2806d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2806d-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2806d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2806d-105">Methods</span></span>  
 <span data-ttu-id="2806d-106">Třída MustUnderstandBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="2806d-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2806d-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2806d-107">Properties</span></span>  
 <span data-ttu-id="2806d-108">Třída MustUnderstandBehavior má následující vlastnost:</span><span class="sxs-lookup"><span data-stu-id="2806d-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="2806d-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="2806d-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="2806d-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2806d-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="2806d-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2806d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2806d-112">Když `true`, všechny hlavičky protokolu SOAP s `MustUnderstand` atribut, který nezabývá způsobit chování pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="2806d-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2806d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2806d-113">Requirements</span></span>  
  
|<span data-ttu-id="2806d-114">MOF</span><span class="sxs-lookup"><span data-stu-id="2806d-114">MOF</span></span>|<span data-ttu-id="2806d-115">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2806d-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2806d-116">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="2806d-116">Namespace</span></span>|<span data-ttu-id="2806d-117">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2806d-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2806d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2806d-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
