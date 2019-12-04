---
title: Odebrání stavu zobrazení, který Návrhář přidá do souboru XAML – WF
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f431275140e821aa5ec4d2235322f06be87d5ee2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715610"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>Odebrání stavu zobrazení, který Návrhář přidá do souboru XAML

Tento příklad ukazuje, jak vytvořit třídu, která je odvozena z <xref:System.Xaml.XamlWriter> a odebírá stav zobrazení ze souboru XAML. Windows Návrhář postupu provádění zapisuje informace do dokumentu XAML, který se označuje jako stav zobrazení. Stav zobrazení odkazuje na informace, které jsou požadovány v době návrhu, jako je například umístění rozložení, které není nutné za běhu. Návrhář postupu provádění vloží tyto informace do dokumentu XAML, jak je upravováno. Návrhář postupu provádění zapíše stav zobrazení do souboru XAML pomocí atributu `mc:Ignorable`, takže tyto informace nejsou načteny, pokud modul runtime načte soubor XAML. Tento příklad ukazuje, jak vytvořit třídu, která odebere informace o stavu zobrazení při zpracovávání uzlů XAML.

## <a name="discussion"></a>Účely

Tato ukázka předvádí, jak vytvořit vlastní zapisovač.

Chcete-li vytvořit vlastní zapisovač XAML, vytvořte třídu, která dědí z <xref:System.Xaml.XamlWriter>. Protože moduly pro zápis XAML jsou často vnořené, je typický sledovat "vnitřní" zapisovač XAML. Tyto "interní" zapisovače lze představit jako odkaz na zbývající zásobník modulů pro zápis XAML, což vám umožní mít více vstupních bodů pro práci a potom delegovat zpracování na zbytek zásobníku.

V této ukázce je k dispozici několik položek zájmu. Jedna z nich kontroluje, jestli je položka napsaná z oboru názvů návrháře. Všimněte si, že tento postup také odříznout použití jiných typů z oboru názvů návrháře v pracovním postupu.

```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)
{
    return xamlMember.IsAttachable &&
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);
}

const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.
public ViewStateCleaningWriter(XamlWriter innerWriter)
{
    this.InnerWriter = innerWriter;
    this.MemberStack = new Stack<XamlMember>();
}

XamlWriter InnerWriter {get; set; }
Stack<XamlMember> MemberStack {get; set; }
```

Tím se také vytvoří zásobník členů XAML, které se používají při procházení datového proudu uzlu. Zbývající práce této ukázky je převážně obsažena v `WriteStartMember` metodě.

```csharp
public override void WriteStartMember(XamlMember xamlMember)
{
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))
    {
        m_attachedPropertyDepth++;
    }

    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteStartMember(xamlMember);
}
```

Následná metoda pak zkontroluje, zda jsou stále obsažena v kontejneru stavu zobrazení, a pokud ano, vrátí a neprojde uzel dolů v zásobníku zapisovače.

```csharp
public override void WriteValue(Object value)
{
    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteValue(value);
}
```

Chcete-li použít vlastní zapisovač XAML, musíte ho zřetězit dohromady v zásobníku zapisovačů XAML. Následující kód ukazuje, jak to lze použít.

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení ViewStateCleaningWriter. sln.

2. Otevřete příkazový řádek a přejděte do adresáře, kde je ViewStageCleaningWriter. exe sestaven.

3. Spusťte ViewStateCleaningWriter. exe v souboru Workflow1. XAML.

   Syntaxe pro spustitelný soubor je uvedena v následujícím příkladu.

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   Výstupem je soubor XAML pro \[souboru], který obsahuje všechny informace o stavu zobrazení, které byly odebrány.

> [!NOTE]
> U <xref:System.Activities.Statements.Sequence>ho pracovního postupu se odeberou několik pomocných parametrů virtualizace. To způsobí, že návrhář přepočítá rozložení při příštím načtení. Když použijete tuto ukázku pro <xref:System.Activities.Statements.Flowchart>, všechny informace o umístění a směrování na řádku se odeberou a při následném načítání do návrháře se všechny aktivity načítají na levou stranu obrazovky.

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>Vytvoření ukázkového souboru XAML pro použití s touto ukázkou

1. Otevřete Visual Studio 2010.

2. Vytvoří novou konzolovou aplikaci pracovního postupu.

3. Přetažení několika aktivit na plátno

4. Uložte soubor XAML pracovního postupu.

5. Zkontrolujte soubor XAML, abyste viděli vlastnosti stavu zobrazení připojené.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
