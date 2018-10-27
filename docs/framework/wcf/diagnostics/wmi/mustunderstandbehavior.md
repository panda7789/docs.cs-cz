---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 0f3efc446104a1afff507f6e7d2cd8c01c4ed417
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452596"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="b1ead-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="b1ead-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="b1ead-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="b1ead-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ead-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1ead-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b1ead-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b1ead-105">Methods</span></span>  
 <span data-ttu-id="b1ead-106">Třída MustUnderstandBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="b1ead-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b1ead-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b1ead-107">Properties</span></span>  
 <span data-ttu-id="b1ead-108">Třída MustUnderstandBehavior má následující vlastnost:</span><span class="sxs-lookup"><span data-stu-id="b1ead-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="b1ead-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="b1ead-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="b1ead-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="b1ead-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="b1ead-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b1ead-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1ead-112">Když `true`, všechna SOAP záhlaví s `MustUnderstand` atributu, která nejsou ovládány způsobí, že chování vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="b1ead-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1ead-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1ead-113">Requirements</span></span>  
  
|<span data-ttu-id="b1ead-114">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="b1ead-114">MOF</span></span>|<span data-ttu-id="b1ead-115">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b1ead-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b1ead-116">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b1ead-116">Namespace</span></span>|<span data-ttu-id="b1ead-117">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b1ead-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1ead-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1ead-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
