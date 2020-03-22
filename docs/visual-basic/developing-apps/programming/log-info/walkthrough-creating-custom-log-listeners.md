---
title: Vytváření vlastních součástí naslouchajících protokolům
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353613"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>Návod: Vytváření vlastních součástí naslouchajících protokolům (Visual Basic)

Tento návod ukazuje, jak vytvořit vlastní naslouchací proces `My.Application.Log` protokolu a nakonfigurovat jej tak, aby poslouchat výstup objektu.

## <a name="getting-started"></a>Začínáme

Posluchači protokolu musí <xref:System.Diagnostics.TraceListener> dědit z třídy.

#### <a name="to-create-the-listener"></a>Vytvoření naslouchací proces

- V aplikaci vytvořte `SimpleListener` třídu s <xref:System.Diagnostics.TraceListener>názvem, která dědí z .

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     Metody <xref:System.Diagnostics.TraceListener.Write%2A> <xref:System.Diagnostics.TraceListener.WriteLine%2A> a vyžadované `MsgBox` základní třídou volají k zobrazení jejich vstupu.

     Atribut <xref:System.Security.Permissions.HostProtectionAttribute> je použit <xref:System.Diagnostics.TraceListener.Write%2A> na <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody a tak, aby jejich atributy odpovídaly metodám základní třídy. Atribut <xref:System.Security.Permissions.HostProtectionAttribute> umožňuje hostiteli, který spouští kód k určení, že kód zveřejňuje synchronizaci ochrany hostitele.

    > [!NOTE]
    > Atribut <xref:System.Security.Permissions.HostProtectionAttribute> je účinný pouze u nespravovaných aplikací, které hostují modul runtime společného jazyka a které implementují ochranu hostitele, například SQL Server.

Chcete-li `My.Application.Log` zajistit, že používá naslouchací proces protokolu, měli byste důrazně pojmenovat sestavení, které obsahuje naslouchací proces protokolu.

Další postup poskytuje některé jednoduché kroky pro vytvoření sestavení silně pojmenované protokol naslouchací proces. Další informace naleznete v [tématu Vytváření a používání sestavení se silným názvem](../../../../standard/assembly/create-use-strong-named.md).

#### <a name="to-strongly-name-the-log-listener-assembly"></a>Silně pojmenovat sestavení posluchače protokolu

1. V **Průzkumníku řešení**je vybrán projekt . V nabídce **Projekt** zvolte **Vlastnosti**.

2. Klikněte na kartu **Podpis.**

3. Vyberte podepsat pole **sestavy.**

4. V ** \<** rozevíracím seznamu Zvolte Nový>v rozevíracím seznamu **Zvolit soubor klíče silného názvu.**

     Otevře se dialogové okno **Vytvořit klíč silného názvu.**

5. Zadejte název souboru klíče do pole **Název souboru klíče.**

6. Zadejte heslo do polí **Zadat heslo** a **Potvrdit heslo.**

7. Klikněte na tlačítko **OK**.

8. Znovu sestavte aplikaci.

## <a name="adding-the-listener"></a>Přidání naslouchací proces

Nyní, když sestavení má silný název, je třeba určit silný `My.Application.Log` název naslouchací proces tak, že používá posluchače protokolu.

Formát silně pojmenovaného typu je následující.

\<název>, \<název sestavení \<>, \<číslo verze \<>,> jazykové verze,>

#### <a name="to-determine-the-strong-name-of-the-listener"></a>Chcete-li určit silný název naslouchací proces

- Následující kód ukazuje, jak určit silně pojmenovaný `SimpleListener`název typu pro .

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     Silný název typu závisí na projektu.

S silným názvem můžete přidat naslouchací proces do kolekce naslouchací `My.Application.Log` proces protokolu.

#### <a name="to-add-the-listener-to-myapplicationlog"></a>Přidání naslouchací proces do My.Application.Log

1. Klikněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a zvolte **Otevřít**.

     -nebo-

     Pokud existuje soubor app.config:

    1. V nabídce **Projekt** zvolte **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.

    3. Klikněte na **Přidat**.

2. Vyhledejte `<listeners>` oddíl v `<source>` části `name` s atributem "DefaultSource", který se nachází v `<sources>` sekci. Sekce `<sources>` je umístěna `<system.diagnostics>` v sekci, v `<configuration>` sekci nejvyšší úrovně.

3. Přidejte tento `<listeners>` prvek do oddílu:

    ```xml
    <add name="SimpleLog" />
    ```

4. Vyhledejte `<sharedListeners>` oddíl v `<system.diagnostics>` části v části `<configuration>` nejvyšší úrovně.

5. Přidejte tento `<sharedListeners>` prvek do tohoto oddílu:

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     Změňte hodnotu `SimpleLogStrongName` má být silný název naslouchací proces.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
