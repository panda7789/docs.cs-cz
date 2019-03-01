---
title: Vytváření vlastních součástí naslouchajících protokolům (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 6bd950b1648bdf0b0c4673f2a90d67086b338ecd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974767"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>Návod: Vytváření vlastních součástí naslouchajících protokolům (Visual Basic)
Tento návod ukazuje, jak vytvořit vlastní protokol naslouchací proces a nakonfigurujte ho tak, aby naslouchala na výstupu `My.Application.Log` objektu.  
  
## <a name="getting-started"></a>Začínáme  
 Součásti naslouchající protokolům musí dědit z <xref:System.Diagnostics.TraceListener> třídy.  
  
#### <a name="to-create-the-listener"></a>Chcete-li vytvořit naslouchací proces  
  
-   Ve vaší aplikaci, vytvořte třídu s názvem `SimpleListener` , která dědí z <xref:System.Diagnostics.TraceListener>.  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     <xref:System.Diagnostics.TraceListener.Write%2A> a <xref:System.Diagnostics.TraceListener.WriteLine%2A> volání metody základní třídy, vyžaduje `MsgBox` zobrazíte svůj vstup.  
  
     <xref:System.Security.Permissions.HostProtectionAttribute> Atribut aplikován <xref:System.Diagnostics.TraceListener.Write%2A> a <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody tak, aby jejich atributy odpovídají metody základní třídy. <xref:System.Security.Permissions.HostProtectionAttribute> Atribut umožňuje hostiteli, který spouští kód určující, že kód poskytuje ochranu hostitel synchronizace.  
  
    > [!NOTE]
    >  <xref:System.Security.Permissions.HostProtectionAttribute> Atribut je platná pouze v nespravovaných aplikacích, které jsou hostiteli modulu common language runtime a, které implementují ochranu hostitele, jako je SQL Server.  
  
 Chcete-li zajistit `My.Application.Log` používá vaše naslouchací proces protokolu důrazně by měl název sestavení, které obsahuje váš protokol naslouchacího procesu.  
  
 Následující postup obsahuje několika jednoduchými kroky pro vytvoření sestavení silným názvem naslouchacího procesu protokolu. Další informace najdete v tématu [vytvoření a použití sestavení](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a>Důrazně název naslouchacího procesu protokolu sestavení  
  
1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídce zvolte **vlastnosti**.   
  
2.  Klikněte na tlačítko **podepisování** kartu.  
  
3.  Vyberte **podepsat sestavení** pole.  
  
4.  Vyberte  **\<nový >** z **vyberte soubor klíče se silným názvem** rozevíracího seznamu.  
  
     **Vytvořit klíč se silným názvem** zobrazí se dialogové okno.  
  
5.  Zadejte název souboru klíče **název souboru klíče** pole.  
  
6.  Zadejte heslo **zadejte heslo** a **potvrzení hesla** polí.  
  
7.  Klikněte na **OK**.  
  
8.  Znovu sestavte aplikaci.  
  
## <a name="adding-the-listener"></a>Přidání posluchače  
 Teď, když sestavení se silným názvem, budete muset určit silný název naslouchacího procesu tak, aby `My.Application.Log` používá vašemu naslouchacímu procesu protokolu.  
  
 Formát typu silným názvem je následujícím způsobem.  
  
 \<Název typu >, \<název sestavení >, \<číslo verze >, \<jazykové verze >, \<silného názvu >  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a>Chcete-li zjistit silný název naslouchacího procesu  
  
-   Následující kód ukazuje, jak určit název silným názvem typu `SimpleListener`.  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     Silný název typu závisí na vašem projektu.  
  
 Se silným názvem, můžete přidat posluchače `My.Application.Log` shromažďování protokolů naslouchací proces.  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a>Chcete-li přidat naslouchací proces pro My.Application.Log  
  
1.  Klikněte pravým tlačítkem na app.config **Průzkumníka řešení** a zvolte **otevřít**.  
  
     -nebo-  
  
     Pokud je soubor app.config:  
  
    1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
    2.  Z **přidat novou položku** dialogového okna zvolte **konfiguračního souboru aplikace**.  
  
    3.  Klikněte na **Přidat**.  
  
2.  Vyhledejte `<listeners>` sekci `<source>` části s `name` atribut "DefaultSource" v `<sources>` oddílu. `<sources>` Je umístěna v `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.  
  
3.  Přidání tohoto elementu `<listeners>` části:  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  Vyhledejte `<sharedListeners>` sekci `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.  
  
5.  Přidejte tento element, který `<sharedListeners>` části:  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     Změňte hodnotu vlastnosti `SimpleLogStrongName` silný název naslouchacího procesu.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Návod: Změna, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
