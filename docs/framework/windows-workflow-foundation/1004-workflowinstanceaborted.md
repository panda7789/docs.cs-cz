---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485184"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="135f3-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="135f3-102">1004 - WorkflowInstanceAborted</span></span>

## <a name="properties"></a><span data-ttu-id="135f3-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="135f3-103">Properties</span></span>

|||
|-|-|
|<span data-ttu-id="135f3-104">ID</span><span class="sxs-lookup"><span data-stu-id="135f3-104">ID</span></span>|<span data-ttu-id="135f3-105">1004</span><span class="sxs-lookup"><span data-stu-id="135f3-105">1004</span></span>|
|<span data-ttu-id="135f3-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="135f3-106">Keywords</span></span>|<span data-ttu-id="135f3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="135f3-107">WFRuntime</span></span>|
|<span data-ttu-id="135f3-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="135f3-108">Level</span></span>|<span data-ttu-id="135f3-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="135f3-109">Information</span></span>|
|<span data-ttu-id="135f3-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="135f3-110">Channel</span></span>|<span data-ttu-id="135f3-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="135f3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|

## <a name="description"></a><span data-ttu-id="135f3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="135f3-112">Description</span></span>

<span data-ttu-id="135f3-113">Označuje, že instance pracovního postupu byl zrušen s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="135f3-113">Indicates a workflow instance has aborted with an exception.</span></span>

## <a name="message"></a><span data-ttu-id="135f3-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="135f3-114">Message</span></span>

<span data-ttu-id="135f3-115">WorkflowInstance Id: '%1' byl zrušen s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="135f3-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>

## <a name="details"></a><span data-ttu-id="135f3-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="135f3-116">Details</span></span>

|<span data-ttu-id="135f3-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="135f3-117">Data Item Name</span></span>|<span data-ttu-id="135f3-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="135f3-118">Data Item Type</span></span>|<span data-ttu-id="135f3-119">Popis</span><span class="sxs-lookup"><span data-stu-id="135f3-119">Description</span></span>|
|--------------------|--------------------|-----------------|
|<span data-ttu-id="135f3-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="135f3-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="135f3-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="135f3-121">The instance id for the workflow</span></span>|
|<span data-ttu-id="135f3-122">Výjimka</span><span class="sxs-lookup"><span data-stu-id="135f3-122">Exception</span></span>|`xs:string`|<span data-ttu-id="135f3-123">Podrobnosti o výjimce pro výjimku</span><span class="sxs-lookup"><span data-stu-id="135f3-123">The exception details for the exception</span></span>|
|<span data-ttu-id="135f3-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="135f3-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="135f3-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="135f3-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
