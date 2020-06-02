---
title: Školicí materiály Azure pro tvůrce modelů
description: Příručka k prostředkům pro Azure Machine Learning
ms.topic: reference
ms.date: 06/01/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: d9eb5560ef33f8f80dbe53e17087c606a8697378
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289470"
---
# <a name="model-builder-azure-training-resources"></a>Školicí materiály Azure pro tvůrce modelů

Následuje návod, který vám pomůže získat další informace o prostředcích používaných ke výukě modelů v Azure pomocí Tvůrce modelů.

## <a name="what-is-an-azure-machine-learning-experiment"></a>Co je Azure Machine Learning experiment?

Azure Machine Learning experiment je prostředek, který je potřeba vytvořit před spuštěním školení tvůrce modelů v Azure.

Experiment zapouzdřuje konfiguraci a výsledky pro jedno nebo více školicích běhů pro strojové učení. Experimenty patří do konkrétního pracovního prostoru. Při prvním vytvoření experimentu je jeho název zaregistrován v pracovním prostoru. Jakákoli následná spuštění – Pokud se používá stejný název experimentu – jsou protokolovány jako součást stejného experimentu. V opačném případě se vytvoří nový experiment.

## <a name="what-is-an-azure-machine-learning-workspace"></a>Co je Azure Machine Learning pracovní prostor?

Pracovní prostor je Azure Machine Learning prostředek, který poskytuje centrální místo pro všechny prostředky Azure Machine Learning a artefakty vytvořené v rámci školicích běhů.

Chcete-li vytvořit pracovní prostor Azure Machine Learning, jsou potřeba následující:

- Name (název): název pracovního prostoru mezi 3-33 znaky. Názvy mohou obsahovat pouze alfanumerické znaky a spojovníky.
- Oblast: geografické umístění datového centra, do kterého se nasadí váš pracovní prostor a prostředky. Doporučuje se zvolit umístění blízko místa, kde jste vy nebo vaši zákazníci.
- Skupina prostředků: kontejner, který obsahuje všechny související prostředky pro řešení Azure.

## <a name="what-is-an-azure-machine-learning-compute"></a>Co je Azure Machine Learning COMPUTE?

Azure Machine Learning COMPUTE je cloudový virtuální počítač se systémem Linux, který se používá pro školení.

Chcete-li vytvořit pracovní prostor Azure Machine Learning, jsou potřeba následující:

- Name (název): název pracovního prostoru mezi 2-16 znaky. Názvy mohou obsahovat pouze alfanumerické znaky a spojovníky.
- Velikost výpočetního prostředí

    Tvůrce modelů může používat jeden z následujících výpočetních typů optimalizovaný pro procesory GPU:

    | Velikost | Virtuální procesory | Paměť: GiB | Dočasné úložiště (SSD): GiB | GPU | Paměť GPU: GiB | Max. datových disků | Maximální počet síťových karet |
    |---|---|---|---|---|---|---|---|
    | Standard_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standard_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    Další podrobnosti o výpočetních typech optimalizovaných pro procesory GPU najdete v [dokumentaci k virtuálním počítačům s řadou NC-Series Linux](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) .
- Priorita výpočtů

  - Nízká priorita: hodí se pro úlohy s kratší dobou spuštění. Může mít vliv na přerušení a nedostatek dostupnosti. Obvykle je méně nákladná, protože využívá nadbytečné kapacity v Azure.
  - Vyhrazeno: vhodné pro úlohy jakékoli doby trvání, ale zejména dlouhotrvající úlohy. Nemá vliv na přerušení nebo nedostatek dostupnosti. Obvykle se náklady vyhradí, protože rezervuje vyhrazenou sadu výpočetních prostředků v Azure pro vaše úkoly.

## <a name="training"></a>Školení

Školení v Azure je dostupné jenom pro scénář klasifikace imagí v Tvůrci modelů. Algoritmus používaný ke výukě těchto modelů je rozsáhlá neuronové síť založená na architektuře ResNet50. Školicí proces trvá určitou dobu a množství času se může lišit v závislosti na velikosti vybraného výpočetního prostředí i na množství dat. Při prvním školení modelu můžete očekávat trochu delší dobu školení, protože je potřeba zřídit prostředky. Průběh spuštění můžete sledovat výběrem odkazu monitorovat aktuální spuštění v Azure Portal v aplikaci Visual Studio.

## <a name="results"></a>Výsledky

Po dokončení školení se do řešení přidají dva projekty s následujícími příponami:

- *ConsoleApp*: Konzolová aplikace C# .NET Core, která poskytuje počáteční kód pro sestavení kanálu předpovědi a vytvoření předpovědi.
- *Model*: .NET Standard aplikace v C#, která obsahuje datové modely definující schéma vstupních a výstupních dat modelu a také následující prostředky:

  - bestModel. Onnx: serializovaná verze modelu ve formátu Open neuronové Network Exchange (ONNX). ONNX je open source formát pro modely AI, který podporuje interoperabilitu mezi platformami, jako je ML.NET, PyTorch a TensorFlow.
  - bestModelMap. JSON: seznam kategorií používaných při vytváření předpovědi k mapování výstupu modelu na textovou kategorii.
  - MLModel. zip: serializovaná verze kanálu předpovědi ML.NET, která používá serializovanou verzi modelu *bestModel. Onnx* k vytvoření předpovědi a mapování výstupů pomocí `bestModelMap.json` souboru.

## <a name="use-the-machine-learning-model"></a>Použití modelu Machine Learning

`ModelInput`Třídy a `ModelOutput` v projektu *modelu* definují schéma očekávaného vstupu a výstupu modelu.

Ve scénáři klasifikace obrázku `ModelInput` obsahuje dva sloupce:

- `ImageSource`: Cesta k řetězci umístění obrázku.
- `Label`: Skutečná kategorie, do které obrázek patří. `Label`se používá jako vstup pouze při výuce a není nutné jej zadávat při provádění předpovědi.

`ModelOutput`Obsahuje dva sloupce:

- `Prediction`: Předpokládaná kategorie obrázku.
- `Score`: Seznam pravděpodobností pro všechny kategorie (nejvyšší patří do `Prediction` ).

## <a name="troubleshooting"></a>Řešení potíží

### <a name="cannot-create-compute"></a>Nejde vytvořit výpočetní prostředky.

Pokud dojde k chybě během Azure Machine Learning vytváření výpočetních prostředků, výpočetní prostředek může stále existovat v chybovém stavu. Pokud se pokusíte znovu vytvořit výpočetní prostředek se stejným názvem, operace se nezdařila. Chcete-li tuto chybu vyřešit, postupujte takto:

- Vytvoření nového COMPUTE s jiným názvem
- Přejít na Azure Portal a odebrat původní výpočetní prostředek
