---
title: MustUnderstandBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dca98f1d8d5f868285ecf11c01122f795ee6cfd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="02f1f-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="02f1f-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="02f1f-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="02f1f-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02f1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02f1f-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="02f1f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="02f1f-105">Methods</span></span>  
 <span data-ttu-id="02f1f-106">Třída MustUnderstandBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="02f1f-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="02f1f-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="02f1f-107">Properties</span></span>  
 <span data-ttu-id="02f1f-108">Třída MustUnderstandBehavior má následující vlastnost:</span><span class="sxs-lookup"><span data-stu-id="02f1f-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="02f1f-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="02f1f-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="02f1f-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="02f1f-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="02f1f-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="02f1f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02f1f-112">Když `true`, všechny hlavičky protokolu SOAP s `MustUnderstand` atribut, který nezabývá způsobit chování pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="02f1f-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02f1f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02f1f-113">Requirements</span></span>  
  
|<span data-ttu-id="02f1f-114">MOF</span><span class="sxs-lookup"><span data-stu-id="02f1f-114">MOF</span></span>|<span data-ttu-id="02f1f-115">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="02f1f-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="02f1f-116">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="02f1f-116">Namespace</span></span>|<span data-ttu-id="02f1f-117">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="02f1f-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02f1f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="02f1f-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
