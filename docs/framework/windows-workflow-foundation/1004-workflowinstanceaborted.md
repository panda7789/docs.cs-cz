---
title: 1004 – WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008613"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="23828-102">1004 – WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="23828-102">1004 - WorkflowInstanceAborted</span></span>

## <a name="properties"></a><span data-ttu-id="23828-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="23828-103">Properties</span></span>

|||
|-|-|
|<span data-ttu-id="23828-104">ID</span><span class="sxs-lookup"><span data-stu-id="23828-104">ID</span></span>|<span data-ttu-id="23828-105">1004</span><span class="sxs-lookup"><span data-stu-id="23828-105">1004</span></span>|
|<span data-ttu-id="23828-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="23828-106">Keywords</span></span>|<span data-ttu-id="23828-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="23828-107">WFRuntime</span></span>|
|<span data-ttu-id="23828-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="23828-108">Level</span></span>|<span data-ttu-id="23828-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="23828-109">Information</span></span>|
|<span data-ttu-id="23828-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="23828-110">Channel</span></span>|<span data-ttu-id="23828-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="23828-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|

## <a name="description"></a><span data-ttu-id="23828-112">Popis</span><span class="sxs-lookup"><span data-stu-id="23828-112">Description</span></span>

<span data-ttu-id="23828-113">Označuje, že instance pracovního postupu byl zrušen s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="23828-113">Indicates a workflow instance has aborted with an exception.</span></span>

## <a name="message"></a><span data-ttu-id="23828-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="23828-114">Message</span></span>

<span data-ttu-id="23828-115">WorkflowInstance Id: '%1' byl zrušen s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="23828-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>

## <a name="details"></a><span data-ttu-id="23828-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="23828-116">Details</span></span>

|<span data-ttu-id="23828-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="23828-117">Data Item Name</span></span>|<span data-ttu-id="23828-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="23828-118">Data Item Type</span></span>|<span data-ttu-id="23828-119">Popis</span><span class="sxs-lookup"><span data-stu-id="23828-119">Description</span></span>|
|--------------------|--------------------|-----------------|
|<span data-ttu-id="23828-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="23828-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="23828-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="23828-121">The instance id for the workflow</span></span>|
|<span data-ttu-id="23828-122">Výjimka</span><span class="sxs-lookup"><span data-stu-id="23828-122">Exception</span></span>|`xs:string`|<span data-ttu-id="23828-123">Podrobnosti o výjimce pro výjimku</span><span class="sxs-lookup"><span data-stu-id="23828-123">The exception details for the exception</span></span>|
|<span data-ttu-id="23828-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="23828-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="23828-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="23828-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
