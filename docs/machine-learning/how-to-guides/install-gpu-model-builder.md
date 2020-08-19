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
# <a name="how-to-install-gpu-support-in-model-builder"></a>Instalace podpory GPU v Tvůrci modelů

Naučte se instalovat ovladače GPU pro použití GPU pomocí Tvůrce modelů.

## <a name="prerequisites"></a>Předpoklady

- Rozšíření sady Visual Studio pro tvůrce modelů. Rozšíření je integrováno do sady Visual Studio jako verze 16.6.1.
- [Rozšíření podpory GPU sady Visual Studio pro tvůrce modelů](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU)
- Nejméně jeden grafický procesor kompatibilní s CUDA. Seznam kompatibilních grafických procesorů GPU najdete v tématu [Průvodce NVIDIA](https://developer.nvidia.com/cuda-gpus).
- Vývojářský účet NVIDIA Pokud žádné nemáte, [vytvořte si bezplatný účet](https://developer.nvidia.com/developer-program).

## <a name="install-dependencies"></a>Instalace závislostí

1. Nainstalujte [CUDA v 10.0](https://developer.nvidia.com/cuda-10.0-download-archive). Ujistěte se, že instalujete CUDA v 10.0, ne žádnou další novější verzi. Nemůžete mít nainstalovanou více verzí CUDA.
1. Nainstalujte [cuDNN v 7.6.4 pro CUDA 10,0](https://developer.nvidia.com/rdp/cudnn-download). Nemůžete mít nainstalovanou více verzí cuDNN. Po stažení souboru ZIP cuDNN v 7.6.4 a jeho rozbalení zkopírujte `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` do `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin` .

## <a name="troubleshooting"></a>Řešení potíží

**Návody víte, jaký GPU mám?**

Postupujte podle uvedených pokynů:

1. Pravým tlačítkem myši klikněte na Desktop.
1. Pokud v překryvném okně vidíte "ovládací panel NVIDIA" nebo "NVIDIA Display", máte grafický procesor NVIDIA
1. V automaticky otevíraném okně klikněte na ovládací panel NVIDIA nebo na zobrazení NVIDIA.
1. Podívejte se na informace o grafické kartě.
1. Zobrazí se název GPU NVIDIA.

**Nevidím ovládací panel NVIDIA (nebo se nepodaří otevřít), ale mám vědět, že mám GPU GPU.**

1. Otevřete Správce zařízení.
1. Podívejte se na zobrazované adaptéry.
1. Nainstalujte vhodný [ovladač](https://www.nvidia.com/drivers) pro grafický procesor.
