---
title: Soubor zadaný v názvu souboru není platný soubor XML
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 89499b07e767bd0b3a777db4e5155f64a4357f0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58921270"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Soubor zadaný v názvu souboru není platný soubor XML

Název souboru, který jste zadali, není platný soubor XML. K určení povolených struktuře a obsahu dokumentu XML, můžete dokumentu typ definice (DTD), Microsoft XML-Data Reduced (XDR) schématu nebo jazyk (XSD) schématu definice schématu XML. XSD schémata jsou preferovaným způsobem, jak určit gramatiky XML v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].

> [!NOTE]
> V některých dřívějších verzích sady Visual Studio **XML – návrhář** se návrhář pro typové datové sady a schématu XML. **XML – návrhář** je stále možné vytvářet a upravovat soubory schémat XML. V sadě Visual Studio 2012, návrháře pro vytváření a úpravu typové datové sady je ale **Návrhář Dataset**. Další informace najdete v tématu [vytváření a úpravy typované datové sady](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).

## <a name="to-correct-this-error"></a>Oprava této chyby

- Zkontrolujte, že zadáváte správný název souboru.

- Zkontrolujte, zda zadaný soubor obsahuje platný kód XML načtením souboru XML, který chcete zkontrolovat do **XML – návrhář**. Z **XML** nabídky, klikněte na tlačítko **ověřit XML**. Chyby zobrazují v **seznamu úkolů**.

- Pokud má soubor XML přidružené schéma XML, zkontrolujte, že se elementy zobrazí ve struktuře definovaná a, obsah jednotlivých prvků odpovídá deklarovanému datovému typy určená ve schématu.

## <a name="see-also"></a>Viz také:

- <xref:System.Xml>
- [Postupy: Analýza cest k souborům](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)