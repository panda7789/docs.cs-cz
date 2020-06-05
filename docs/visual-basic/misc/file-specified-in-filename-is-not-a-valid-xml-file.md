---
title: Soubor zadaný v souboru FileName není platný soubor XML.
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: a84042490935e3e7e5a6de2a802d9effd5b4d3d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358345"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Soubor zadaný v souboru FileName není platný soubor XML.

Název souboru, který jste zadali, není platný soubor XML. Chcete-li určit povolenou strukturu a obsah dokumentu XML, můžete použít definici typu dokumentu (DTD), schéma XDR (Microsoft XML-data redukovaný) nebo schéma XML Schema Definition Language (XSD). Schémata XSD jsou preferovaným způsobem, jak určit gramatiky XML v .NET Framework.

> [!NOTE]
> V některých starších verzích sady Visual Studio je **Návrhář XML** návrhářem pro typové datové sady a schéma XML. **Návrhář XML** lze nadále použít k vytvoření a úpravě souborů schémat XML. V sadě Visual Studio 2012 je však Návrhář pro vytváření a úpravu typových datových sad **Návrhář datových sad**. Další informace najdete v tématu [vytváření a úpravy zadaných datových sad](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).

## <a name="to-correct-this-error"></a>Oprava této chyby

- Ověřte, zda jste zadali správný název souboru.

- Ověřte, zda zadaný soubor obsahuje platný kód XML načtením souboru XML, který chcete vrátit do **Návrháře XML**. V nabídce **XML** klikněte na **ověřit XML**. V **seznam úkolů**se zobrazují chyby.

- Pokud má soubor XML přidružené schéma XML, ověřte, zda se prvky zobrazí v definované struktuře a zda obsah jednotlivých prvků odpovídá deklarovaným datovým typům, které jsou zadány ve schématu.

## <a name="see-also"></a>Viz také

- <xref:System.Xml>
- [Postupy: Analýza cest k souborům](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
