---
title: 'Postupy: Vytváření, inicializace a konfigurace přepínačů trasování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
ms.openlocfilehash: 8bf3b974ff0ef9f719274ab684b3dce85295c917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181830"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Postupy: Vytváření, inicializace a konfigurace přepínačů trasování
Přepínače trasování umožňují povolit, zakázat a filtrovat výstup trasování.  
  
<a name="create"></a>
## <a name="creating-and-initializing-a-trace-switch"></a>Vytvoření a inicializace přepínače trasování  
 Chcete-li použít přepínače trasování, musíte je nejprve vytvořit a umístit do kódu. Existují dvě předdefinované třídy, ze kterých <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> můžete <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> vytvořit objekty přepínače: třída a třída. Použili <xref:System.Diagnostics.BooleanSwitch> byste, pokud vám záleží pouze na tom, zda se zobrazí zpráva o trasování; které byste <xref:System.Diagnostics.TraceSwitch> použili, pokud chcete rozlišovat mezi úrovněmi trasování. Pokud používáte <xref:System.Diagnostics.TraceSwitch>, můžete definovat vlastní ladicí zprávy a přidružit je k různým úrovním trasování. Oba typy přepínačů můžete použít s trasováním nebo laděním. Ve výchozím <xref:System.Diagnostics.BooleanSwitch> nastavení je <xref:System.Diagnostics.TraceSwitch> a zakázána <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>a je nastavena na úroveň . Přepínače trasování lze vytvořit a umístit do libovolné části kódu, který je může používat.  
  
 Přestože můžete nastavit úrovně trasování a další možnosti konfigurace v kódu, doporučujeme použít konfigurační soubor ke správě stavu přepínačů. Je to proto, že správa konfigurace přepínačů v konfiguračním systému poskytuje větší flexibilitu – můžete zapnout a vypnout různé přepínače a změnit úrovně bez nutnosti opětovné kompilace aplikace.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>Vytvoření a inicializaci přepínače trasování  
  
1. Definujte přepínač jako <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> typ <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> nebo typ a nastavte název a popis přepínače.  
  
2. Nakonfigurujte přepínač trasování. Další informace naleznete [v tématu Konfigurace přepínačů trasování](#configure).  
  
     Následující kód vytvoří dva přepínače, jeden z každého typu:  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =
       new System.Diagnostics.TraceSwitch("General",
       "Entire application");  
    ```  
  
<a name="configure"></a>
## <a name="configuring-trace-switches"></a>Konfigurace přepínačů trasování  
 Po distribuci aplikace můžete stále povolit nebo zakázat výstup trasování konfigurací trasovacích přepínačů v aplikaci. Konfigurace přepínače znamená změnu jeho hodnoty z externího zdroje po jeho inicializací. Pomocí konfiguračního souboru můžete změnit hodnoty objektů přepínače. Nakonfigurujete přepínač trasování, abyste jej zapínali a vypínali nebo nastavili jeho úroveň a určili množství a typ zpráv, které předává posluchačům.  
  
 Přepínače jsou konfigurovány pomocí souboru .config. Pro webovou aplikaci se jedná o soubor Web.config přidružený k projektu. V aplikaci systému Windows je tento soubor pojmenován (název aplikace).exe.config. V nasazené aplikaci musí být tento soubor umístěn ve stejné složce jako spustitelný soubor.  
  
 Když aplikace spustí kód, který vytvoří instanci přepínače poprvé, zkontroluje konfigurační soubor informace o úrovni trasování o pojmenované přepínači. Systém trasování zkontroluje konfigurační soubor pouze jednou pro konkrétní přepínač – při prvním spuštění aplikace přepínač.  
  
 V nasazené aplikaci povolíte trasovací kód změnou konfigurace objektů přepínače, když vaše aplikace není spuštěna. Obvykle to zahrnuje zapnutí a vypnutí objektů přepínače nebo změnou úrovní trasování a restartování aplikace.  
  
 Když vytvoříte instanci přepínače, inicializujete ji také zadáním dvou argumentů: argumentu *displayName* a argumentu *popisu.* Argument *displayName* konstruktoru <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> nastaví vlastnost <xref:System.Diagnostics.Switch> instance třídy. *DisplayName* je název, který se používá ke konfiguraci přepínače v souboru .config a argument *description* by měl vrátit stručný popis přepínače a zpráv, které řídí.  
  
 Kromě zadání názvu přepínače ke konfiguraci je nutné zadat také hodnotu přepínače. Tato hodnota je celé číslo. Pro <xref:System.Diagnostics.BooleanSwitch>hodnota 0 odpovídá **Off**a jakákoli nenulová hodnota odpovídá **On**. Pro <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3 a 4 odpovídají **Off**, **Error**, **Warning**, **Info**a **Verbose**, resp. Jakékoli číslo větší než 4 je považováno za **podrobné**a jakékoli číslo menší než nula je považováno za **Off**.  
  
> [!NOTE]
> V rozhraní .NET Framework verze 2.0 můžete použít text k určení hodnoty přepínače. Například `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo text představující hodnotu výčtu, <xref:System.Diagnostics.TraceSwitch>například `Error` pro . Řádek `<add name="myTraceSwitch" value="Error" />` je ekvivalentní `<add name="myTraceSwitch" value="1" />`.  
  
 Aby koncoví uživatelé mohli konfigurovat trasovací přepínače aplikace, musíte poskytnout podrobnou dokumentaci o přepínačích ve vaší aplikaci. Měli byste podrobně popsat, které přepínače řídí, co a jak je zapínat a vypínat. Měli byste také poskytnout koncovému uživateli soubor .config, který má příslušnou nápovědu v komentářích.  
  
#### <a name="to-configure-trace-switches"></a>Konfigurace přepínačů trasování  
  
1. Chcete-li použít přepínače trasování, musíte je nejprve vytvořit a umístit do kódu, jak je popsáno v části [Vytvoření a inicializace přepínače trasování](#create).  
  
2. Pokud projekt neobsahuje konfigurační soubor (app.config nebo Web.config), pak z nabídky **Projekt** vyberte **Přidat novou položku**.  
  
    - **Visual Basic:** V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.  
  
         Konfigurační soubor aplikace je vytvořen a otevřen. Jedná se o dokument XML, jehož kořenový prvek je`<configuration>.`  
  
    - **Vizuální jazyk C#:** V dialogovém okně **Přidat novou položku** zvolte **Soubor XML**. Pojmenujte tento soubor **app.config**. V editoru XML přidejte za deklaraci XML následující XML:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Při kompilaci projektu je soubor app.config zkopírován do výstupní složky projektu a přejmenován *na název_aplikace*.exe.config.  
  
3. Za `<configuration>` značku, ale `</configuration>` před značku, přidejte příslušný XML pro konfiguraci přepínačů. Následující příklady ukazují **BooleanSwitch** s Vlastnost `DataMessageSwitch` **DisplayName** a **TraceSwitch** s `TraceLevelSwitch` **DisplayName** vlastnost .  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     V této konfiguraci jsou oba přepínače vypnuty.  
  
4. Pokud potřebujete zapnout **Přepínač BooleanSwitch** `DataMessagesSwitch` , jak je znázorněno v předchozím příkladu, změňte **hodnotu** na libovolné celé číslo než 0.  
  
5. Pokud potřebujete zapnout **TraceSwitch**, `TraceLevelSwitch` jak je znázorněno v předchozím příkladu, změňte **hodnotu** na příslušnou úroveň nastavení (1 až 4).  
  
6. Přidejte komentáře do souboru .config, aby koncový uživatel měl jasnou představu o tom, jaké hodnoty změnit pro vhodnou konfiguraci přepínačů.  
  
     Následující příklad ukazuje, jak může vypadat konečný kód, včetně komentářů:  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a>Viz také

- [Trasování a instrumentace aplikací](tracing-and-instrumenting-applications.md)
- [Postupy: Přidání příkazů trasování do kódu aplikace](how-to-add-trace-statements-to-application-code.md)
- [Přepínače trasování](trace-switches.md)
- [Trasování a ladění schématu nastavení](../configure-apps/file-schema/trace-debug/index.md)
