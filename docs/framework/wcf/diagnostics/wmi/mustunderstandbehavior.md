---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 334bab97a04ed464dce6944692b04a9ed1295296
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613818"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="d0c0f-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="d0c0f-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="d0c0f-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="d0c0f-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0c0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0c0f-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d0c0f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d0c0f-105">Methods</span></span>  
 <span data-ttu-id="d0c0f-106">Třída MustUnderstandBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d0c0f-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d0c0f-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d0c0f-107">Properties</span></span>  
 <span data-ttu-id="d0c0f-108">Třída MustUnderstandBehavior má následující vlastnost:</span><span class="sxs-lookup"><span data-stu-id="d0c0f-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="d0c0f-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="d0c0f-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="d0c0f-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="d0c0f-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="d0c0f-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d0c0f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0c0f-112">Když `true`, všechna SOAP záhlaví s `MustUnderstand` atributu, která nejsou ovládány způsobí, že chování vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="d0c0f-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0c0f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0c0f-113">Requirements</span></span>  
  
|<span data-ttu-id="d0c0f-114">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="d0c0f-114">MOF</span></span>|<span data-ttu-id="d0c0f-115">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d0c0f-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d0c0f-116">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d0c0f-116">Namespace</span></span>|<span data-ttu-id="d0c0f-117">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d0c0f-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0c0f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0c0f-118">See also</span></span>
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
