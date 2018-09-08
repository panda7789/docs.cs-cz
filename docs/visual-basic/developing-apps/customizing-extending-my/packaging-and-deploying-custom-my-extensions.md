---
title: Balení a nasazení vlastních rozšíření oboru názvů My (Visual Basic)
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 4212f58c39f63be6ba20c3b79e5d9c98d0615c5e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211772"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>Zabalení a nasazení vlastních rozšíření oboru názvů My (Visual Basic)

Visual Basic poskytuje jednoduchý způsob nasazení vaší vlastní `My` rozšíření oboru názvů pomocí šablony sady Visual Studio. Pokud vytváříte šablonu projektu pro kterou vaše `My` rozšíření jsou nedílnou součástí toho nový typ projektu, můžete zahrnout pouze váš vlastní `My` kódu rozšíření s projektem při exportu šablony. Další informace o exportu šablony projektů, naleznete v tématu [postupy: vytváření šablon projektu](/visualstudio/ide/how-to-create-project-templates).

Pokud vaše vlastní `My` rozšíření je v souboru jednoho kódu, můžete exportovat soubor šablony položky, které uživatelé můžou přidávat na libovolný typ projektu jazyka Visual Basic. Potom můžete přizpůsobit šablonu položky povolit další funkce a chování pro vaše vlastní `My` rozšíření v projektu jazyka Visual Basic. Tyto možnosti patří:

- Umožňuje uživatelům spravovat své vlastní `My` rozšíření **Moje rozšíření** stránky Návrháře projektu jazyka Visual Basic.

- Automatické přidávání vlastních `My` rozšíření při odkazu na zadané sestavení se přidá do projektu.

- Skrytí `My` šablonu položky rozšíření v **přidat položku** dialogové okno tak, aby není zahrnutý v seznamu položek projektu.

Toto téma popisuje, jak zabalit vlastní `My` rozšíření jako skrytá položka šablonu, která se dají spravovat z **Moje rozšíření** stránky Návrháře projektu jazyka Visual Basic. Vlastní `My` rozšíření můžete také přidat automaticky při přidání do projektu odkaz na zadané sestavení.

## <a name="create-a-my-namespace-extension"></a>Vytvoření rozšíření rozhraní My namespace

Prvním krokem při vytváření balíčku pro nasazení, aby vlastní `My` rozšíření je pro vytvoření rozšíření jako soubor jeden kód. Podrobnosti a pokyny o tom, jak vytvořit vlastní `My` rozšíření, naleznete v tématu [rozšíření My Namespace v jazyce Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Exportovat rozšíření rozhraní My namespace jako šablonu položky

Až budete mít soubor kódu, který obsahuje vaše `My` rozšíření oboru názvů, můžete exportovat soubor kódu jako šablonu položky sady Visual Studio. Pokyny o tom, jak exportovat soubor jako šablonu položky sady Visual Studio najdete v tématu [postupy: vytváření šablon položek](/visualstudio/ide/how-to-create-item-templates).

> [!NOTE]
> Pokud vaše `My` rozšíření oboru názvů závislý na konkrétní sestavení, můžete přizpůsobit vaši šablonu položky automaticky instalovat vaši `My` rozšíření oboru názvů při přidání odkazu na toto sestavení. Díky tomu budete chtít vyloučit tento odkaz na sestavení, když je soubor kódu exportovat jako šablonu položky sady Visual Studio.

## <a name="customize-the-item-template"></a>Přizpůsobení šablony položky

Můžete povolit položku šablony pro správu z **Moje rozšíření** stránky Návrháře projektu jazyka Visual Basic. Můžete také povolit šablony položky se automaticky přidá, když se do projektu přidá odkaz na zadané sestavení. Pokud chcete povolit tyto úpravy, přidáte nový soubor, Soubor CustomData do šablony a pak přidejte nový prvek do souboru XML v souboru .vstemplate.

### <a name="add-the-customdata-file"></a>Přidat soubor CustomData

Soubor CustomData je textový soubor, který má příponu názvu souboru. CustomData (název souboru lze nastavit na libovolnou hodnotu smysluplné do šablony), který obsahuje XML. Kód XML v souboru CustomData instruuje Visual Basic pro zahrnutí vaší `My` rozšíření uživatelé budou používat **Moje rozšíření** stránky Návrháře projektu jazyka Visual Basic. Volitelně můžete přidat <`AssemblyFullName>` atribut CustomData souboru XML. Toto dá pokyn jazyka Visual Basic můžete automaticky nainstalovat vlastní `My` rozšíření při odkazu na konkrétní sestavení je přidána do projektu. Můžete použít libovolný textového editoru nebo editoru XML k vytvoření souboru CustomData a poté jej přidejte do šablony položky komprimovanou složku (ZIP).

Například následující kód XML ukazuje obsah souboru CustomData, který se přidá šablonu položky do složky Moje rozšíření systému projektu jazyka Visual Basic, pokud odkaz na sestavení Microsoft.VisualBasic.PowerPacks.Vs.dll se přidá do projektu.

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

Obsahuje soubor CustomData <`VBMyExtensionTemplate>` element, který má atributy, jak je uvedeno v následující tabulce.

|Atribut|Popis|
|---|---|
|`ID`|Požadováno. Jedinečný identifikátor pro rozšíření. Pokud rozšíření, která má toto ID již byla přidána do projektu, uživatel nebude vyzván znovu přidat.|
|`Version`|Požadováno. Číslo verze pro šablonu položky.|
|`AssemblyFullName`|Volitelné. Název sestavení. Když do projektu se přidá odkaz na toto sestavení, uživateli zobrazí výzva k přidání `My` rozšíření z této šablony položky.|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Přidat \<CustomDataSignature > element k souboru .vstemplate

K identifikaci vaší šablony položky sady Visual Studio `My` rozšíření oboru názvů, musíte také upravit soubor .vstemplate šablony položky. Je nutné přidat `<CustomDataSignature>` elementu `<TemplateData>` elementu. `<CustomDataSignature>` Element musí obsahovat text `Microsoft.VisualBasic.MyExtension`, jak je znázorněno v následujícím příkladu.

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

Soubory v komprimované složce (.zip soubor) nemůžete upravovat přímo. Musí zkopírovat soubor .vstemplate ze složky komprimované, upravte ho a soubor .vstemplate v komprimované složce nahraďte aktualizovanou kopii.

Následující příklad ukazuje obsah souboru .vstemplate, který má `<CustomDataSignature>` element přidat.

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a>Instalace šablony

Instalace šablony, můžete zkopírovat komprimovanou složku (*ZIP* soubor) do složky šablony položky Visual Basic. Ve výchozím nastavení, šablon položek uživatele jsou umístěny v *%USERPROFILE%\Documents\Visual Studio \<verze\>\Templates\ItemTemplates\Visual Basic*. Alternativně můžete publikovat šablony jako instalační program Visual Studio (*.vsi*) soubor.

## <a name="see-also"></a>Viz také:

- [Rozšíření My Namespace v jazyce Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [Rozšíření aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [Přizpůsobení výběru objektů dostupných v oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Stránka Moje rozšíření, Návrhář projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
