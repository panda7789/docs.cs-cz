---
title: Soubor zadaný v názvu souboru není platný soubor XML
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 3aecb0c2c87539717656a29f5b48f94fce3c8453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639185"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Soubor zadaný v názvu souboru není platný soubor XML
Název souboru, který jste zadali, není platný soubor XML. Chcete-li určit povolené struktuře a obsahu dokumentu XML, můžete použít definice typu dokumentu (DTD), schéma Microsoft XML-Data Reduced (XDR) nebo schématu schématu XML definition language (XSD). XSD schémata jsou upřednostňovaný způsob, jak určit gramatika XML v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  V některé starší verze sady Visual Studio **XML návrhář** je návrháře pro typové datové sady a schématu XML. **XML návrhář** stále umožňuje vytvářet a upravovat soubory schématu XML. Ale v [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], je návrháře pro vytváření a úpravy typové datové sady **návrháře Dataset**. Další informace najdete v tématu [vytváření a úpravy typovaných datových sad](/visualstudio/data-tools/creating-and-editing-typed-datasets).  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte, že jsou poskytuje správný název souboru.  
  
-   Zkontrolujte, zda zadaný soubor obsahuje platný kód XML načtením souboru XML, který chcete zkontrolovat do **XML návrhář**. Z **XML** nabídky, klikněte na tlačítko **ověřit XML**. Chyby zobrazují v **seznam úkolů**.  
  
-   Pokud soubor XML má přidružené schéma XML, zkontrolujte, že se objeví elementy ve struktuře definované a že obsah jednotlivých prvků odpovídá deklarované datové typy, určená ve schématu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml>  
 [Postupy: Analýza cest k souborům](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
