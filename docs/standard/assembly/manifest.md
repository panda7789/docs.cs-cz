---
title: Manifest sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
ms.openlocfilehash: f1913f8c41ba4a7b54f7abcdfb97400503da8ac5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73107154"
---
# <a name="assembly-manifest"></a>Manifest sestavení
Každé sestavení, statické nebo dynamické, obsahuje kolekci dat, která popisuje, jak se prvky v sestavení vzájemně vztahují. Manifest sestavení obsahuje metadata tohoto sestavení. Manifest sestavení obsahuje všechna metadata potřebná k určení požadavků na verzi sestavení a identity zabezpečení a všechna metadata potřebná k definování rozsahu sestavení a vyřešení odkazů na prostředky a třídy. Manifest sestavení může být uložen v souboru PE *(exe* nebo *.dll)* s kódem zprostředkujícího jazyka Microsoft (MSIL) nebo v samostatném souboru PE, který obsahuje pouze informace o manifestu sestavení.  
  
 Následující obrázek znázorňuje různé způsoby, jak může být manifest uložen.  
  
 ![Diagram, který zobrazuje manifest v sestavení s jedním souborem a konfiguraci sestavení více souborů.](./media/manifest/assembly-types-diagram.gif)  
  
 Pro sestavení s jedním přidruženým souborem je manifest začleněn do souboru PE a tvoří sestavení s jedním souborem. Můžete vytvořit vícesouborové sestavení se samostatným souborem manifestu nebo s manifestem začleněným do jednoho ze souborů PE v sestavení.  
  
 Manifest každého sestavení provádí následující funkce:  
  
- Vytvoří vyjmenovává soubory, které tvoří sestavení.  
  
- Určuje, jak se odkazy na typy sestavení a prostředky mapovat na soubory, které obsahují jejich deklarace a implementace.  
  
- Vyjmenovává další sestavy, na kterých závisí sestava.  
  
- Poskytuje úroveň dereference mezi příjemci sestavení a podrobnosti implementace sestavení.  
  
- Vykreslí sestavení self-describing.  
  
## <a name="assembly-manifest-contents"></a>Obsah manifestu sestavení  
 V následující tabulce jsou uvedeny informace obsažené v manifestu sestavení. První čtyři položky: název sestavení, číslo verze, jazyková verze a informace o silném názvu tvoří identitu sestavení.  
  
|Informace|Popis|  
|-----------------|-----------------|  
|Název sestavení|Textový řetězec určující název sestavení.|  
|Číslo verze|Číslo hlavní a dílčí verze a číslo revize a sestavení. Běžný jazyk runtime používá tato čísla k vynucení zásad verze.|  
|Culture|Informace o jazykové verzi nebo jazyk, který sestavení podporuje. Tyto informace by měly být použity pouze k označení sestavení jako satelitní sestavení obsahující informace specifické pro jazykovou verzi nebo jazyk. (Sestavení s informacemi o jazykové verzi se automaticky považuje za satelitní sestavení.)|  
|Informace o silném názvu|Veřejný klíč od vydavatele, pokud sestavení byl udělen silný název.|  
|Seznam všech souborů v sestavě|Hash každého souboru obsaženého v sestavení a název souboru. Všimněte si, že všechny soubory, které tvoří sestavení musí být ve stejném adresáři jako soubor obsahující manifest sestavení.|  
|Informace o odkazu na typ|Informace používané za běhu mapovat odkaz na typ souboru, který obsahuje jeho deklarace a implementace. Používá se pro typy, které jsou exportovány ze sestavy.|  
|Informace o odkazovaných sestaveních|Seznam dalších sestavení, na která sestavení staticky odkazuje. Každý odkaz obsahuje název závislého sestavení, metadata sestavení (verze, jazyková verze, operační systém a tak dále) a veřejný klíč, pokud je sestavení silné s názvem.|  
  
 Některé informace v manifestu sestavení můžete přidat nebo změnit pomocí atributů sestavení v kódu. Můžete změnit informace o verzi a informační atributy, včetně ochranné známky, autorských práv, produktu, společnosti a informační verze. Úplný seznam atributů sestavení naleznete v tématu [Nastavení atributů sestavení](set-attributes.md).  
  
## <a name="see-also"></a>Viz také

- [Obsah sestavení](contents.md)
- [Správa verzí sestavení](versioning.md)
- [Vytváření satelitních sestavení](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Sestavení se silným názvem](strong-named.md)
