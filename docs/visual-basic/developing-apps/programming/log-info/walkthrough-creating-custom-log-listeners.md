---
title: Vytváření vlastních protokolových posluchačů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 90135074a4d34ea73743faffb2531305fcb326fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965264"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>Návod: Vytváření vlastních protokolových posluchačů (Visual Basic)
Tento návod ukazuje, jak vytvořit vlastní naslouchací proces protokolu a nakonfigurovat ho tak, aby naslouchal výstupu `My.Application.Log` objektu.  
  
## <a name="getting-started"></a>Začínáme  
 Naslouchací procesy protokolu musí dědit od <xref:System.Diagnostics.TraceListener> třídy.  
  
#### <a name="to-create-the-listener"></a>Vytvoření naslouchacího procesu  
  
- V aplikaci vytvořte třídu s názvem `SimpleListener` , která dědí z. <xref:System.Diagnostics.TraceListener>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     Metody <xref:System.Diagnostics.TraceListener.Write%2A> `MsgBox` a <xref:System.Diagnostics.TraceListener.WriteLine%2A> , které jsou požadovány pro základní třídu, volají pro zobrazení jejich vstupu.  
  
     Atribut se aplikuje <xref:System.Diagnostics.TraceListener.Write%2A> na metody a <xref:System.Diagnostics.TraceListener.WriteLine%2A> , aby jejich atributy odpovídaly metodám základní třídy. <xref:System.Security.Permissions.HostProtectionAttribute> <xref:System.Security.Permissions.HostProtectionAttribute> Atribut umožňuje hostiteli, který spouští kód, určit, že kód zveřejňuje synchronizaci hostitele.  
  
    > [!NOTE]
    > <xref:System.Security.Permissions.HostProtectionAttribute> Atribut je platný pouze v nespravovaných aplikacích, které jsou hostiteli modulu CLR (Common Language Runtime) a které implementují ochranu hostitele, například SQL Server.  
  
 Chcete-li `My.Application.Log` zajistit, aby používala naslouchací proces protokolu, měli byste silně pojmenovat sestavení, které obsahuje váš naslouchací proces protokolu.  
  
 Další postup poskytuje několik jednoduchých kroků pro vytvoření silně pojmenovaného sestavení naslouchacího procesu protokolu. Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a>Pro silně pojmenování sestavení naslouchacího procesu protokolu  
  
1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.   
  
2. Klikněte na kartu **podepisování** .  
  
3. Vyberte pole **podepsat sestavení** .  
  
4. V rozevíracím seznamu **Vyberte soubor klíče se silným názvem** vyberte  **\<nový >** .  
  
     Otevře se dialogové okno **vytvořit klíč se silným názvem** .  
  
5. Zadejte název souboru klíče do pole **název souboru klíče** .  
  
6. Do polí **Zadejte** heslo a **potvrďte heslo** zadejte heslo.  
  
7. Klikněte na **OK**.  
  
8. Znovu sestavte aplikaci.  
  
## <a name="adding-the-listener"></a>Přidání naslouchacího procesu  
 Nyní, když má sestavení silný název, je nutné určit silný název naslouchacího procesu tak, `My.Application.Log` aby používal naslouchací proces protokolu.  
  
 Formát silně pojmenovaného typu je následující.  
  
 \<název typu >, \<název sestavení >, \<číslo verze >, \<jazyková verze > \<, silný název >  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a>Určení silného názvu naslouchacího procesu  
  
- Následující kód ukazuje, jak určit název silně pojmenovaného typu pro `SimpleListener`.  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     Silný název typu závisí na vašem projektu.  
  
 Se silným názvem můžete přidat naslouchací proces do `My.Application.Log` kolekce log-Listener.  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a>Přidání naslouchacího procesu do My. Application. log  
  
1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.  
  
     -nebo-  
  
     Pokud existuje soubor App. config:  
  
    1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.  
  
    2. V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.  
  
    3. Klikněte na **Přidat**.  
  
2. Vyhledejte část v části s `name` atributem "DefaultSource", který se nachází v části.`<sources>` `<source>` `<listeners>` Oddíl je umístěný `<system.diagnostics>` v části v části nejvyšší úrovně `<configuration>`. `<sources>`  
  
3. Přidejte tento element do `<listeners>` oddílu:  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4. `<sharedListeners>` Vyhledejte část `<system.diagnostics>` v části v sekci nejvyšší úrovně `<configuration>` .  
  
5. Přidejte tento element do této `<sharedListeners>` části:  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     Změňte hodnotu `SimpleLogStrongName` na se silným názvem naslouchacího procesu.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolovat výjimky](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Návod: Změna místa, kam aplikace My. Application. Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
