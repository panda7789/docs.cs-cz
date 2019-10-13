---
title: Ladění pracovních postupů
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: 3947e61161b0e2108fa48fbc7e33fb7601645a1b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291485"
---
# <a name="debugging-workflows"></a>Ladění pracovních postupů

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] nabízí několik možností pro ladění spuštěných pracovních postupů z vývojového prostředí. Pracovní postupy lze ladit v návrháři, v jazyce XAML a v kódu.

## <a name="debugging-in-the-workflow-designer"></a>Ladění v Návrhář postupu provádění

Zarážky lze pro aktivity v Návrháři postupu nastavit buď zvýrazněním aktivity, stisknutím klávesy <kbd>F9</kbd> nebo pomocí místní nabídky aktivity. Spuštění pracovního postupu pak dojde k přerušení, pokud je hostitel pracovního postupu spuštěn v režimu ladění. Na následujícím snímku obrazovky je spuštění pracovního postupu pozastaveno na zarážce. Další informace najdete v tématu [ladění pracovních postupů pomocí Návrhář postupu provádění](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).

## <a name="debugging-in-xaml"></a>Ladění v jazyce XAML

Pokud byl pracovní postup pozastaven na zarážce v návrháři, může být pracovní postup také laděn v jazyce XAML. Chcete-li zobrazit bod provádění v jazyce XAML, vyberte v Návrháři pracovního postupu možnost **zobrazení XAML** při pozastavení provádění pracovního postupu. Ladění lze přepnout zpět do návrháře tím, že znovu otevřete pracovní postup v Návrháři z Průzkumníka řešení. Další informace naleznete v tématu [How to: Debug XAML with Návrhář postupu provádění](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).

## <a name="debugging-in-code"></a>Ladění v kódu

Chcete-li nastavit zarážku, klikněte na levý okraj podokna Code (kód), nebo stiskněte klávesu <kbd>F9</kbd> se kurzorem na řádku, kde jej chcete nastavit.

## <a name="attaching-to-a-workflow-process"></a>Připojení k procesu pracovního postupu

Ladění pracovního postupu také podporuje použití infrastruktury sady Visual Studio pro připojení k procesu. To umožňuje autorovi pracovního postupu ladit pracovní postup běžící v jiném hostitelském prostředí, například Internetová informační služba (IIS) 7,0.

## <a name="remote-debugging"></a>Vzdálené ladění

Vzdálené ladění programovací model Windows Workflow Foundation (WF) funguje stejně jako vzdálené ladění pro jiné součásti sady Visual Studio. Informace o použití vzdáleného ladění naleznete v tématu [How to: Enable Remote Debugging](https://go.microsoft.com/fwlink/?LinkId=196257).

> [!NOTE]
> Pokud je aplikace pracovního postupu cílena na architekturu x86 a je hostována v počítači s 64 bitovým operačním systémem, nebude vzdálené ladění fungovat, pokud není nainstalována aplikace Visual Studio na vzdáleném počítači, nebo cíl pro aplikaci pracovního postupu se změní na **Libovolný procesor**.

## <a name="extending-the-workflow-debugging-service"></a>Rozšíření služby ladění pracovního postupu

Služba pracovního postupu pro pracovní postup je teď veřejná a dá se použít k vytvoření vlastních aplikací, jako je monitorování, simulace a ladění v novém hostovaném návrháři. Další informace najdete v článku o @no__t 0.
