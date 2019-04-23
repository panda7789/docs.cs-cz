---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 7e6a96c217b038e870b4e865315766afa3b3c757
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975342"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="24f3b-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="24f3b-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="24f3b-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="24f3b-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24f3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24f3b-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="24f3b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="24f3b-105">Methods</span></span>  
 <span data-ttu-id="24f3b-106">Třída MustUnderstandBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="24f3b-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="24f3b-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="24f3b-107">Properties</span></span>  
 <span data-ttu-id="24f3b-108">Třída MustUnderstandBehavior má následující vlastnost:</span><span class="sxs-lookup"><span data-stu-id="24f3b-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="24f3b-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="24f3b-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="24f3b-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="24f3b-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="24f3b-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="24f3b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="24f3b-112">Když `true`, všechna SOAP záhlaví s `MustUnderstand` atributu, která nejsou ovládány způsobí, že chování vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="24f3b-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24f3b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24f3b-113">Requirements</span></span>  
  
|<span data-ttu-id="24f3b-114">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="24f3b-114">MOF</span></span>|<span data-ttu-id="24f3b-115">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="24f3b-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="24f3b-116">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="24f3b-116">Namespace</span></span>|<span data-ttu-id="24f3b-117">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="24f3b-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24f3b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24f3b-118">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
