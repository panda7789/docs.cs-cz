---
title: Školicí prostředky Azure tvůrce modelů
description: Průvodce materiály pro Azure Machine Learning
ms.topic: reference
ms.date: 02/27/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a19e13955d0eaea344109eb817f3a3959c3dd883
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185824"
---
# <a name="model-builder-azure-training-resources"></a>Školicí prostředky Azure tvůrce modelů

Následuje průvodce, který vám pomůže získat další informace o prostředcích používaných k trénování modelů v Azure pomocí Tvůrce modelů.

## <a name="what-is-an-azure-machine-learning-experiment"></a>Co je experiment Azure Machine Learning?

Experiment Azure Machine Learning je prostředek, který je potřeba vytvořit před spuštěním školení Tvůrce modelů v Azure.

Experiment zapouzdřuje konfiguraci a výsledky pro jeden nebo více spuštění školení strojového učení. Experimenty patří do určitého pracovního prostoru. Při prvním vytvoření experimentu je jeho název zaregistrován v pracovním prostoru. Všechny následné spuštění - pokud je použit stejný název experimentu - jsou zaznamenány jako součást stejného experimentu. V opačném případě je vytvořen nový experiment.

## <a name="what-is-an-azure-machine-learning-workspace"></a>Co je pracovní prostor Azure Machine Learning?

Pracovní prostor je prostředek Azure Machine Learning, který poskytuje centrální místo pro všechny prostředky Azure Machine Learning a artefakty vytvořené jako součást trénovacího běhu.

K vytvoření pracovního prostoru Azure Machine Learning jsou povinné následující:

- Název: Název pracovního prostoru mezi 3 až 33 znaky. Názvy mohou obsahovat pouze alfanumerické znaky a pomlčky.
- Oblast: Geografické umístění datového centra, do kterého se nasazuje váš pracovní prostor a prostředky. Doporučujeme zvolit místo v blízkosti místa, kde se nacházíte vy nebo vaši zákazníci.
- Skupina prostředků: Kontejner, který obsahuje všechny související prostředky pro řešení Azure.

## <a name="what-is-an-azure-machine-learning-compute"></a>Co je výpočetní prostředky Azure Machine Learning?

Výpočetní prostředky Azure Machine Learning je cloudový virtuální počítač s Linuxem používaný pro školení.

K vytvoření pracovního prostoru Azure Machine Learning jsou povinné následující:

- Název: Název pracovního prostoru mezi 2 až 16 znaky. Názvy mohou obsahovat pouze alfanumerické znaky a pomlčky.
- Velikost výpočetních prostředků

    Tvůrce modelů může použít jeden z následujících výpočetních typů optimalizovaných pro GPU:

    | Velikost | Virtuální procesory | Paměť: GiB | Dočasné úložiště (SSD): GiB | GPU | Paměť GPU: GiB | Max. datových disků | Maximální počet síťových karet |
    |---|---|---|---|---|---|---|---|
    | Standard_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standard_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    Další podrobnosti o výpočetních typech optimalizovaných pro GPU najdete v dokumentaci k [virtuálním počítačům](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) s Linuxem řady NC.

## <a name="training"></a>Školení

Školení v Azure je k dispozici jenom pro scénář klasifikace image tvůrce modelů. Algoritmus používaný k trénování těchto modelů je Hluboká neuronová síť založená na architektuře ResNet50. Proces školení trvá nějakou dobu a množství času se může lišit v závislosti na velikosti vybraného výpočetního prostředí a také na množství dat. Při prvním trénování modelu můžete očekávat o něco delší dobu školení, protože prostředky musí být zřízeny. Průběh spuštění můžete sledovat tak, že v sadě Visual Studio vyberete odkaz Sledovat aktuální spuštění na portálu Azure.

## <a name="results"></a>Výsledky

Po dokončení školení jsou do vašeho řešení přidány dva projekty s následujícími příponami:

- *ConsoleApp*: C# .NET Core konzoly aplikace, která poskytuje počáteční kód pro sestavení kanálu předpověď a předpovědi.
- *Model*: C# .NET Standardní aplikace, která obsahuje datové modely, které definují schéma vstupních a výstupních dat modelu, stejně jako následující prostředky:

  - bestModel.onnx: Serializovaná verze modelu ve formátu OPEN Neural Network Exchange (ONNX). ONNX je open source formát pro modely AI, který podporuje interoperabilitu mezi frameworky jako ML.NET, PyTorch a TensorFlow.
  - bestModelMap.json: Seznam kategorií používaných při vytváření předpovědí pro mapování výstupu modelu na kategorii textu.
  - MLModel.zip: Serializovaná verze kanálu ML.NET předpověď, který používá serializovanou verzi modelu *bestModel.onnx* k `bestModelMap.json` předpovědi a mapy výstupy pomocí souboru.

## <a name="use-the-machine-learning-model"></a>Použití modelu strojového učení

`ModelInput` Třídy `ModelOutput` a v projektu *Model* definují schéma očekávaného vstupu a výstupu modelu.

Ve scénáři `ModelInput` klasifikace bitových obrázků obsahuje dva sloupce:

- `ImageSource`: Cesta řetězce umístění obrázku.
- `Label`: Skutečná kategorie, do které obrázek patří. `Label`se používá pouze jako vstup při trénování a není nutné poskytnout při vytváření předpovědi.

Obsahuje `ModelOutput` dva sloupce:

- `Prediction`: Předpovídaná kategorie obrázku.
- `Score`: Seznam pravděpodobností pro všechny kategorie (nejvyšší `Prediction`patří do ).

## <a name="troubleshooting"></a>Řešení potíží

### <a name="cannot-create-compute"></a>Nelze vytvořit výpočetní prostředky.

Pokud dojde k chybě během azure machine learning výpočetní ho výpočtu, výpočetní prostředek může stále existovat, v chybovém stavu. Pokud se pokusíte znovu vytvořit výpočetní prostředek se stejným názvem, operace se nezdaří. Chcete-li tuto chybu opravit, buď:

- Vytvoření nového výpočetního výkonu s jiným názvem
- Přejděte na portál Azure a odeberte původní výpočetní prostředek.
