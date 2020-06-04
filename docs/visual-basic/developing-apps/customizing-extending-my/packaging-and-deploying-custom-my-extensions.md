---
title: Balení a nasazení vlastních rozšíření
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 6d2cc2b01b04b30bd3b1a4371352ded20ea8664b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411750"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>Zabalit a nasadit vlastní moje rozšíření (Visual Basic)

Visual Basic poskytuje snadný způsob, jak nasadit vlastní `My` rozšíření oboru názvů pomocí šablon sady Visual Studio. Pokud vytváříte šablonu projektu, pro kterou jsou vaše `My` rozšíření nedílnou součástí nového typu projektu, můžete `My` při exportu šablony do projektu zahrnout pouze vlastní kód rozšíření. Další informace o exportu šablon projektů naleznete v tématu [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).

Pokud je vaše vlastní `My` rozšíření v jednom souboru kódu, můžete soubor exportovat jako šablonu položky, kterou mohou uživatelé přidat do libovolného typu Visual Basic projektu. Pak můžete přizpůsobit šablonu položky a povolit tak další možnosti a chování pro vlastní `My` rozšíření v projektu Visual Basic. Mezi tyto možnosti patří následující:

- Umožnění uživatelům spravovat vlastní `My` rozšíření ze stránky **Moje rozšíření** v Návrháři projektu Visual Basic.

- `My`Pokud se do projektu přidá odkaz na zadané sestavení, automaticky se přidá vlastní rozšíření.

- Skrytí `My` šablony položky rozšíření v dialogovém okně **Přidat položku** tak, aby není zahrnuto v seznamu položek projektu.

Toto téma popisuje, jak zabalit vlastní `My` rozšíření jako skrytou šablonu položky, kterou lze spravovat ze stránky **Moje rozšíření** v Návrháři projektu Visual Basic. Vlastní `My` rozšíření lze také přidat automaticky, pokud je do projektu přidán odkaz na zadané sestavení.

## <a name="create-a-my-namespace-extension"></a>Vytvoření rozšíření My Namespace

Prvním krokem při vytváření balíčku pro nasazení pro vlastní `My` rozšíření je vytvořit rozšíření jako jeden soubor kódu. Podrobnosti a pokyny, jak vytvořit vlastní `My` rozšíření, najdete v tématu [rozšíření oboru názvů My v Visual Basic](extending-the-my-namespace.md).

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Exportovat rozšíření My Namespace jako šablonu položky

Až budete mít soubor kódu, který obsahuje `My` rozšíření oboru názvů, můžete soubor kódu exportovat jako šablonu položky sady Visual Studio. Pokyny, jak exportovat soubor jako šablonu položky sady Visual Studio, naleznete v tématu [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).

> [!NOTE]
> Pokud `My` rozšíření oboru názvů má závislost na konkrétní sestavení, můžete přizpůsobit šablonu položky tak, aby automaticky instalovala `My` rozšíření oboru názvů, když je přidán odkaz na toto sestavení. V důsledku toho budete chtít vyloučit tento odkaz na sestavení, když exportujete soubor kódu jako šablonu položky sady Visual Studio.

## <a name="customize-the-item-template"></a>Přizpůsobení šablony položky

Šablonu položky můžete povolit, aby byla spravována ze stránky **Moje rozšíření** návrháře projektu Visual Basic. Můžete také povolit automatické přidání šablony položky, když je do projektu přidán odkaz na zadané sestavení. Chcete-li povolit tato přizpůsobení, přidejte do šablony nový soubor, označovaný jako soubor CustomData, a poté přidejte nový prvek do XML v souboru. vstemplate.

### <a name="add-the-customdata-file"></a>Přidat soubor CustomData

Soubor CustomData je textový soubor, který má příponu názvu souboru. CustomData (název souboru může být nastaven na libovolnou hodnotu smysluplnou pro šablonu) a obsahující XML. XML v souboru CustomData instruuje Visual Basic, aby zahrnovalo vaše `My` rozšíření, když uživatelé použijí stránku **Moje rozšíření** Návrháře projektu Visual Basic. Volitelně můžete přidat `AssemblyFullName>` atribut <do souboru XML CustomData. Tímto dáte pokyn Visual Basic k automatické instalaci vlastního `My` rozšíření, když je do projektu přidán odkaz na konkrétní sestavení. Pomocí libovolného textového editoru nebo editoru XML můžete vytvořit soubor CustomData a pak ho přidat do komprimované složky šablony položky (soubor ZIP).

Například následující kód XML ukazuje obsah souboru CustomData, který přidá položku šablony do složky Moje rozšíření v projektu Visual Basic, když se do projektu přidá odkaz na sestavení Microsoft. VisualBasic. PowerPacks. vs. dll.

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

Soubor CustomData obsahuje <`VBMyExtensionTemplate>` element, který má atributy uvedené v následující tabulce.

|Atribut|Description|
|---|---|
|`ID`|Povinná hodnota. Jedinečný identifikátor pro rozšíření. Pokud rozšíření s tímto ID již bylo do projektu přidáno, uživatel nebude vyzván k jeho přidání.|
|`Version`|Povinná hodnota. Číslo verze pro šablonu položky|
|`AssemblyFullName`|Nepovinný parametr. Název sestavení. Pokud je do projektu přidán odkaz na toto sestavení, bude uživatel vyzván k přidání `My` rozšíření z této šablony položky.|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Přidat \<CustomDataSignature> element do souboru. vstemplate

Chcete-li identifikovat šablonu položky sady Visual Studio jako `My` rozšíření oboru názvů, je nutné také upravit soubor. vstemplate pro šablonu položky. Je nutné přidat `<CustomDataSignature>` prvek do `<TemplateData>` prvku. `<CustomDataSignature>`Element musí obsahovat text `Microsoft.VisualBasic.MyExtension` , jak je znázorněno v následujícím příkladu.

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

Soubory nelze upravovat v komprimované složce (soubor. zip) přímo. Je nutné zkopírovat soubor. vstemplate z komprimované složky, upravit ho a pak nahradit soubor. vstemplate v komprimované složce pomocí aktualizované kopie.

Následující příklad ukazuje obsah souboru. vstemplate, který má `<CustomDataSignature>` přidaný element.

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

Chcete-li nainstalovat šablonu, můžete zkopírovat komprimovanou složku (soubor *. zip* ) do složky šablony Visual Basic položek. Ve výchozím nastavení se šablony uživatelských položek nacházejí v *%UserProfile%\Documents\Visual studiu \<Version\> \Templates\ItemTemplates\Visual Basic*. Alternativně můžete šablonu publikovat jako soubor Instalační program pro Visual Studio (*. vsi*).

## <a name="see-also"></a>Viz také

- [Rozšíření oboru názvů My v jazyce Visual Basic](extending-the-my-namespace.md)
- [Rozšíření aplikačního modelu jazyka Visual Basic](extending-the-visual-basic-application-model.md)
- [Přizpůsobení výběru objektů dostupných v oboru názvů My](customizing-which-objects-are-available-in-my.md)
- [Stránka Moje rozšíření, návrhář projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
