---
title: "Odebrání stav zobrazení návrháře přidá do souboru XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d9f153d212e1180e5de92a6299d2fbb2d6864c42
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>Odebrání stav zobrazení návrháře přidá do souboru XAML
Tento příklad ukazuje, jak vytvořte třídu, která je odvozena z <xref:System.Windows.Markup.XamlWriter> a odebere zobrazení stavu ze souboru XAML. [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]zapisuje informace do dokumentu XAML, která se označuje jako stav zobrazení. Stav zobrazení odkazuje na informace, který je požadován v době návrhu, jako je například umístění rozložení, který není nutný za běhu. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]Vloží do dokumentu XAML tyto informace, jako je upravit. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]zapisuje do souboru XAML s stav zobrazení `mc:Ignorable` atributů, takže tyto informace není načíst, pokud modul runtime načte souboru XAML. Tento příklad ukazuje, jak vytvořte třídu, která odebere této informace o stavu zobrazení při zpracování uzlů XAML.  
  
## <a name="discussion"></a>Diskusní  
 Tento příklad znázorňuje, jak vytvořit vlastní zapisovač.  
  
 Pokud chcete vytvořit vlastní zapisovač XAML, vytvořte třídu, která dědí z <xref:System.Windows.Markup.XamlWriter>. Jak často jsou vnořené zapisovače XAML, je typické ke sledování "vnitřní" XAML zapisovače. Tyto "vnitřní ' zapisovače si lze představit jako odkaz na zbývající zásobníku zapisovačů XAML, umožní vám tak, aby měl více vstupních bodů k práci a potom delegovat zpracování ke zbytku zásobníku.  
  
 V této ukázce jsou několik položek, které vás zajímají. Jeden je zkontrolujte, zda je položka zapisovaný z Návrháře oboru názvů. Všimněte si, že to taky odstraní na použití jiných typů z Návrháře oboru názvů v pracovním postupu.  
  
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
  
 Tím se vytvoří také zásobník XAML členů, které se používají při procházení datový proud uzlu. Zbývající práce Tato ukázka je součástí z velké části <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` metoda.  
  
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
  
 Následující metody pak zkontrolujte, zda jsou stále obsažené v kontejneru zobrazení stavu a pokud ano, vrátí a nepředávejte uzel dolů v zásobníku zapisovače.  
  
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
  
 Pokud chcete používat vlastní zapisovač XAML, můžete, musí být propojeny ho společně v zásobníku zapisovačů XAML. Následující kód ukazuje, jak je možné používat.  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1. Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ViewStateCleaningWriter.sln.  
  
2. Otevřete příkazový řádek a přejděte do adresáře, kde je založená ViewStageCleaningWriter.exe.  
  
3. Spusťte ViewStateCleaningWriter.exe na soubor Workflow1.xaml.  

   Syntaxe pro spustitelný soubor je znázorněno v následujícím příkladu.  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   Tento soubor XAML pro výstupy \[Výstupní_soubor], která obsahuje všechny zobrazení informací o stavu odebrat.  
  
> [!NOTE]
> Pro <xref:System.Activities.Statements.Sequence> pracovního postupu, počet virtualizace jsou pomocné parametry odebrána. To způsobí, že návrháře přepočítat rozložení další čas, který je načten. Při použití této ukázky pro <xref:System.Activities.Statements.Flowchart>, budou odebrány všechny umístění a směrování informace řádku a na dalších načítání do návrháře přibývají všechny aktivity na levé straně obrazovky.  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>Chcete-li vytvořit a ukázkový soubor XAML pro použití s této ukázky  
  
1. Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2. Vytvořte novou konzolovou aplikaci pracovního postupu.  
  
3. Přetáhnout myší na plátno několik aktivit  
  
4. Uložte soubor XAML workflowu.  
  
5. Zkontrolujte soubor XAML zobrazíte zobrazení stavu přidružené vlastnosti.  
  
> [!IMPORTANT]
> Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
