---
title: Odebrání stavu zobrazení, Návrhář přidá do souboru XAML
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: ed2fda0bb66b2c8fe58c60acc6f80b9e9c8e984e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524949"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>Odebrání stavu zobrazení, Návrhář přidá do souboru XAML
Tento příklad ukazuje, jak vytvořit třídu, která je odvozena z <xref:System.Windows.Markup.XamlWriter> a odebere zobrazit stav ze souboru XAML. [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] zapisuje informace do dokumentu XAML, který je označován jako stav zobrazení. Stav zobrazení odkazuje na informace, které je nutné v době návrhu, jako je například umístění rozložení, které nejsou potřebné v době běhu. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] Vloží tyto informace do dokumentu XAML, jako je upravovat. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] zapíše do souboru XAML s stav zobrazení `mc:Ignorable` atribut, takže tyto informace není načten při načtení modulu runtime XAML souboru. Tento příklad ukazuje, jak vytvořit třídu, která odebere tuto informace o stavu zobrazení při zpracování uzlů XAML.  
  
## <a name="discussion"></a>Diskuse  
 Tento příklad ukazuje, jak vytvořit vlastní zapisovače.  
  
 Pokud chcete vytvořit vlastní zapisovače XAML, vytvořte třídu, která dědí z <xref:System.Windows.Markup.XamlWriter>. Jak často jsou vnořené uživatelé vytvářející obsah XAML, je typické ke sledování "vnitřních" zapisovač XAML. Tyto "vnitřní" zapisovače si lze představit jako odkaz na zbývající zásobníku XAML zapisovačů, díky kterým práci a následně delegovat zpracování na zbývající část zásobníku více vstupních bodů.  
  
 V této ukázce se několik položek, které vás zajímají. Jeden je kontrola ověří, zda je položka zapisovaná z Návrháře oboru názvů. Všimněte si, že to také odstraní použití jiných typů z Návrháře oboru názvů v pracovním postupu.  
  
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
  
 Tím se vytvoří také zásobníku XAML členů, které se používají při rekurzivním průchodu datovém proudu uzlu. Zbývající práce Tato ukázka je součástí do značné míry <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` metody.  
  
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
  
 Následující metody a zkontrolujte, zda jsou stále obsažené v zobrazení stavu kontejneru a pokud ano, vraťte se a nepředávejte uzel dolů zásobníku zapisovače.  
  
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
  
 Pokud chcete použít vlastní zapisovače XAML, musíte provést řetězení společně v zásobníku zapisovačů XAML. Následující kód ukazuje, jak to lze použít.  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1. Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ViewStateCleaningWriter.sln.  
  
2. Otevřete příkazový řádek a přejděte do adresáře, kde je postavená ViewStageCleaningWriter.exe.  
  
3. Spusťte ViewStateCleaningWriter.exe Workflow1.xaml soubor.  

   Syntaxe pro spustitelný soubor je znázorněno v následujícím příkladu.  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   Výstupem soubor XAML, který chcete \[outfile], který má všechna zobrazení informací o stavu odebrána.  
  
> [!NOTE]
> Pro <xref:System.Activities.Statements.Sequence> pracovního postupu, počet virtualizace pomocné parametry se odeberou. To způsobí, že návrhář přepočítat rozložení při příštím načtení. Při použití pro tuto ukázku <xref:System.Activities.Statements.Flowchart>, umístění a směrování informace řádku se odeberou a na následné načítání do návrháře, jsou navršeny všechny aktivity na levé straně obrazovky.  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>K vytvoření ukázkového souboru XAML pro použití s touto ukázkou  
  
1. Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2. Vytvořte novou konzolovou aplikaci pracovního postupu.  
  
3. Přetažení několika aktivity na plátno  
  
4. Uložte soubor XAML pracovního postupu.  
  
5. Zkontrolujte soubor XAML k zobrazení stavu připojené vlastnosti.  
  
> [!IMPORTANT]
> Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
