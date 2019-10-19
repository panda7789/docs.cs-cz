---
title: Vytváření vlastních protokolových posluchačů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 298bfa2987397591492480d953949d20168785bf
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581688"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>Návod: Vytváření vlastních součástí naslouchajících protokolům (Visual Basic)

Tento návod ukazuje, jak vytvořit vlastní naslouchací proces protokolu a nakonfigurovat ho tak, aby naslouchal výstupu objektu `My.Application.Log`.

## <a name="getting-started"></a>Začínáme

Naslouchací procesy protokolu musí dědit z třídy <xref:System.Diagnostics.TraceListener>.

#### <a name="to-create-the-listener"></a>Vytvoření naslouchacího procesu

- V aplikaci vytvořte třídu s názvem `SimpleListener`, která dědí z <xref:System.Diagnostics.TraceListener>.

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     Metody <xref:System.Diagnostics.TraceListener.Write%2A> a <xref:System.Diagnostics.TraceListener.WriteLine%2A> vyžadované základní třídou, volají `MsgBox` pro zobrazení jejich vstupu.

     Atribut <xref:System.Security.Permissions.HostProtectionAttribute> se aplikuje na metody <xref:System.Diagnostics.TraceListener.Write%2A> a <xref:System.Diagnostics.TraceListener.WriteLine%2A>, aby jejich atributy odpovídaly metodám základní třídy. Atribut <xref:System.Security.Permissions.HostProtectionAttribute> umožňuje hostiteli, který spouští kód, určit, že kód zveřejňuje synchronizaci v rámci ochrany hostitele.

    > [!NOTE]
    > Atribut <xref:System.Security.Permissions.HostProtectionAttribute> je platný pouze v nespravovaných aplikacích, které hostují modul CLR (Common Language Runtime) a které implementují ochranu hostitele, jako je například SQL Server.

Chcete-li zajistit, aby `My.Application.Log` používala naslouchací proces protokolu, měli byste silně pojmenovat sestavení, které obsahuje váš naslouchací proces protokolu.

Další postup poskytuje několik jednoduchých kroků pro vytvoření silně pojmenovaného sestavení naslouchacího procesu protokolu. Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../../standard/assembly/create-use-strong-named.md).

#### <a name="to-strongly-name-the-log-listener-assembly"></a>Pro silně pojmenování sestavení naslouchacího procesu protokolu

1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

2. Klikněte na kartu **podepisování** .

3. Vyberte pole **podepsat sestavení** .

4. V rozevíracím seznamu **Vyberte soubor klíče se silným názvem** vyberte možnost **\<New >** .

     Otevře se dialogové okno **vytvořit klíč se silným názvem** .

5. Zadejte název souboru klíče do pole **název souboru klíče** .

6. Do polí **Zadejte** heslo a **potvrďte heslo** zadejte heslo.

7. Klikněte na tlačítko **OK**.

8. Znovu sestavte aplikaci.

## <a name="adding-the-listener"></a>Přidání naslouchacího procesu

Nyní, když má sestavení silný název, je nutné určit silný název naslouchacího procesu, aby `My.Application.Log` používal váš naslouchací proces protokolu.

Formát silně pojmenovaného typu je následující.

\<type název >, \<assembly název >, \<version číslo >, \<culture >, \<strong název >

#### <a name="to-determine-the-strong-name-of-the-listener"></a>Určení silného názvu naslouchacího procesu

- Následující kód ukazuje, jak určit název silně pojmenovaného typu pro `SimpleListener`.

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     Silný název typu závisí na vašem projektu.

Se silným názvem můžete přidat naslouchací proces do kolekce `My.Application.Log` log-Listener.

#### <a name="to-add-the-listener-to-myapplicationlog"></a>Přidání naslouchacího procesu do My. Application. log

1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.

     -nebo-

     Pokud existuje soubor App. config:

    1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.

    3. Klikněte na tlačítko **Přidat**.

2. Vyhledejte část `<listeners>` v části `<source>` s atributem `name` "DefaultSource", který se nachází v části `<sources>`. Část `<sources>` se nachází v části `<system.diagnostics>` v části `<configuration>` nejvyšší úrovně.

3. Přidejte tento prvek do oddílu `<listeners>`:

    ```xml
    <add name="SimpleLog" />
    ```

4. Vyhledejte část `<sharedListeners>` v části `<system.diagnostics>` v části `<configuration>` nejvyšší úrovně.

5. Přidejte tento prvek do tohoto `<sharedListeners>` části:

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     Změňte hodnotu `SimpleLogStrongName` na silný název naslouchacího procesu.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
