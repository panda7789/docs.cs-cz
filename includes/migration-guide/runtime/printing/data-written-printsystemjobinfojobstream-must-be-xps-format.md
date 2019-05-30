---
ms.openlocfilehash: 74f00821f2304664729faa8de2f0163c6611f513
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379620"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>Data zapsaná do PrintSystemJobInfo.JobStream musí být ve formátu XPS

|   |   |
|---|---|
|Podrobnosti|<xref:System.Printing.PrintSystemJobInfo.JobStream> Zpřístupňuje vlastnost datového proudu tiskové úlohy. Uživatel může odesílat nezpracovaná data na základní součásti tisku operačního systému pomocí zápisu s tímto datovým proudem. Od verze rozhraní .NET Framework 4.5 na Windows 8 a novější verze operačního systému Windows, zapsaná data do tohoto datového proudu musí být ve formátu XPS jako datový proud balíčku.|
|Doporučení|Výstup vytisknout obsah, můžete provést jeden z následujících akcí:<ul><li>Použití <xref:System.Windows.Xps.XpsDocumentWriter> třídy do výstupního vytisknout obsah. Toto je Doporučená alternativa.</li><li>Ujistěte se, že data přenášená do datový proud vrácený <xref:System.Printing.PrintSystemJobInfo.JobStream> vlastnost je ve formátu XPS jako datový proud balíčku.</li></ul>|
|Scope|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
