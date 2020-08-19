---
title: Instalace podpory GPU v Tvůrci modelů
description: Informace o tom, jak nainstalovat podporu GPU v Tvůrci modelů
ms.date: 08/18/2020
author: luisquintanilla
ms.author: luquinta
ms.topic: how-to
ms.openlocfilehash: ce629efa4c12a69f87196de35ebfe4331dc0800f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608564"
---
# <a name="how-to-install-gpu-support-in-model-builder"></a><span data-ttu-id="5de59-103">Instalace podpory GPU v Tvůrci modelů</span><span class="sxs-lookup"><span data-stu-id="5de59-103">How to install GPU support in Model Builder</span></span>

<span data-ttu-id="5de59-104">Naučte se instalovat ovladače GPU pro použití GPU pomocí Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="5de59-104">Learn how to install the GPU drivers to use your GPU with Model Builder.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5de59-105">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="5de59-105">Prerequisites</span></span>

- <span data-ttu-id="5de59-106">Rozšíření sady Visual Studio pro tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="5de59-106">Model Builder Visual Studio extension.</span></span> <span data-ttu-id="5de59-107">Rozšíření je integrováno do sady Visual Studio jako verze 16.6.1.</span><span class="sxs-lookup"><span data-stu-id="5de59-107">The extension is built into Visual Studio as of version 16.6.1.</span></span>
- <span data-ttu-id="5de59-108">[Rozšíření podpory GPU sady Visual Studio pro tvůrce modelů](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU)</span><span class="sxs-lookup"><span data-stu-id="5de59-108">[Model Builder Visual Studio GPU support extension](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).</span></span>
- <span data-ttu-id="5de59-109">Nejméně jeden grafický procesor kompatibilní s CUDA.</span><span class="sxs-lookup"><span data-stu-id="5de59-109">At least one CUDA compatible GPU.</span></span> <span data-ttu-id="5de59-110">Seznam kompatibilních grafických procesorů GPU najdete v tématu [Průvodce NVIDIA](https://developer.nvidia.com/cuda-gpus).</span><span class="sxs-lookup"><span data-stu-id="5de59-110">For a list of compatible GPUs, see [NVIDIA's guide](https://developer.nvidia.com/cuda-gpus).</span></span>
- <span data-ttu-id="5de59-111">Vývojářský účet NVIDIA</span><span class="sxs-lookup"><span data-stu-id="5de59-111">NVIDIA developer account.</span></span> <span data-ttu-id="5de59-112">Pokud žádné nemáte, [vytvořte si bezplatný účet](https://developer.nvidia.com/developer-program).</span><span class="sxs-lookup"><span data-stu-id="5de59-112">If you don't have one, [create a free account](https://developer.nvidia.com/developer-program).</span></span>

## <a name="install-dependencies"></a><span data-ttu-id="5de59-113">Instalace závislostí</span><span class="sxs-lookup"><span data-stu-id="5de59-113">Install dependencies</span></span>

1. <span data-ttu-id="5de59-114">Nainstalujte [CUDA v 10.0](https://developer.nvidia.com/cuda-10.0-download-archive).</span><span class="sxs-lookup"><span data-stu-id="5de59-114">Install [CUDA v10.0](https://developer.nvidia.com/cuda-10.0-download-archive).</span></span> <span data-ttu-id="5de59-115">Ujistěte se, že instalujete CUDA v 10.0, ne žádnou další novější verzi.</span><span class="sxs-lookup"><span data-stu-id="5de59-115">Make sure you install CUDA v10.0, not any other newer version.</span></span> <span data-ttu-id="5de59-116">Nemůžete mít nainstalovanou více verzí CUDA.</span><span class="sxs-lookup"><span data-stu-id="5de59-116">You cannot have multiple versions of CUDA installed.</span></span>
1. <span data-ttu-id="5de59-117">Nainstalujte [cuDNN v 7.6.4 pro CUDA 10,0](https://developer.nvidia.com/rdp/cudnn-download).</span><span class="sxs-lookup"><span data-stu-id="5de59-117">Install [cuDNN v7.6.4 for CUDA 10.0](https://developer.nvidia.com/rdp/cudnn-download).</span></span> <span data-ttu-id="5de59-118">Nemůžete mít nainstalovanou více verzí cuDNN.</span><span class="sxs-lookup"><span data-stu-id="5de59-118">You cannot have multiple versions of cuDNN installed.</span></span> <span data-ttu-id="5de59-119">Po stažení souboru ZIP cuDNN v 7.6.4 a jeho rozbalení zkopírujte `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` do `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin` .</span><span class="sxs-lookup"><span data-stu-id="5de59-119">After downloading cuDNN v7.6.4 zip file and unpacking it, copy `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` to `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin`.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="5de59-120">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="5de59-120">Troubleshooting</span></span>

<span data-ttu-id="5de59-121">**Návody víte, jaký GPU mám?**</span><span class="sxs-lookup"><span data-stu-id="5de59-121">**How do I know what GPU I have?**</span></span>

<span data-ttu-id="5de59-122">Postupujte podle uvedených pokynů:</span><span class="sxs-lookup"><span data-stu-id="5de59-122">Follow instructions provided:</span></span>

1. <span data-ttu-id="5de59-123">Pravým tlačítkem myši klikněte na Desktop.</span><span class="sxs-lookup"><span data-stu-id="5de59-123">Right-click on desktop</span></span>
1. <span data-ttu-id="5de59-124">Pokud v překryvném okně vidíte "ovládací panel NVIDIA" nebo "NVIDIA Display", máte grafický procesor NVIDIA</span><span class="sxs-lookup"><span data-stu-id="5de59-124">If you see "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window, you have an NVIDIA GPU</span></span>
1. <span data-ttu-id="5de59-125">V automaticky otevíraném okně klikněte na ovládací panel NVIDIA nebo na zobrazení NVIDIA.</span><span class="sxs-lookup"><span data-stu-id="5de59-125">Click on "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window</span></span>
1. <span data-ttu-id="5de59-126">Podívejte se na informace o grafické kartě.</span><span class="sxs-lookup"><span data-stu-id="5de59-126">Look at "Graphics Card Information"</span></span>
1. <span data-ttu-id="5de59-127">Zobrazí se název GPU NVIDIA.</span><span class="sxs-lookup"><span data-stu-id="5de59-127">You will see the name of your NVIDIA GPU</span></span>

<span data-ttu-id="5de59-128">**Nevidím ovládací panel NVIDIA (nebo se nepodaří otevřít), ale mám vědět, že mám GPU GPU.**</span><span class="sxs-lookup"><span data-stu-id="5de59-128">**I don't see NVIDIA Control Panel (or it fails to open) but I know I have an NVIDIA GPU.**</span></span>

1. <span data-ttu-id="5de59-129">Otevřete Správce zařízení.</span><span class="sxs-lookup"><span data-stu-id="5de59-129">Open Device Manager</span></span>
1. <span data-ttu-id="5de59-130">Podívejte se na zobrazované adaptéry.</span><span class="sxs-lookup"><span data-stu-id="5de59-130">Look at Display adapters</span></span>
1. <span data-ttu-id="5de59-131">Nainstalujte vhodný [ovladač](https://www.nvidia.com/drivers) pro grafický procesor.</span><span class="sxs-lookup"><span data-stu-id="5de59-131">Install appropriate [driver](https://www.nvidia.com/drivers) for your GPU.</span></span>
