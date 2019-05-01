---
title: 1005 – WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008600"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="b072d-102">1005 – WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="b072d-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="b072d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b072d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b072d-104">ID</span><span class="sxs-lookup"><span data-stu-id="b072d-104">ID</span></span>|<span data-ttu-id="b072d-105">1005</span><span class="sxs-lookup"><span data-stu-id="b072d-105">1005</span></span>|  
|<span data-ttu-id="b072d-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b072d-106">Keywords</span></span>|<span data-ttu-id="b072d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b072d-107">WFRuntime</span></span>|  
|<span data-ttu-id="b072d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b072d-108">Level</span></span>|<span data-ttu-id="b072d-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="b072d-109">Information</span></span>|  
|<span data-ttu-id="b072d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b072d-110">Channel</span></span>|<span data-ttu-id="b072d-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="b072d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b072d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b072d-112">Description</span></span>  
 <span data-ttu-id="b072d-113">Označuje, že má nečinný aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b072d-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b072d-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b072d-114">Message</span></span>  
 <span data-ttu-id="b072d-115">WorkflowApplication Id: '%1' Přechod do nečinného režimu.</span><span class="sxs-lookup"><span data-stu-id="b072d-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b072d-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b072d-116">Details</span></span>  
  
|<span data-ttu-id="b072d-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b072d-117">Data Item Name</span></span>|<span data-ttu-id="b072d-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="b072d-118">Data Item Type</span></span>|<span data-ttu-id="b072d-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b072d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b072d-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="b072d-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="b072d-121">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b072d-121">The workflow application id</span></span>|  
|<span data-ttu-id="b072d-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b072d-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b072d-123">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b072d-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
