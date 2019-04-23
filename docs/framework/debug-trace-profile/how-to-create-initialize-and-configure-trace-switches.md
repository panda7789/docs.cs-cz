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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87170035df47e7605d25531df4b0759bf121ad80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325706"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Postupy: Vytváření, inicializace a konfigurace přepínačů trasování
Přepínače trasování umožňují povolit, zakázat a filtrovat výstup trasování.  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a>Vytváření a inicializace přepínačů trasování  
 Chcete-li použít přepínačů trasování, musíte je vytvořit a umístit je do vašeho kódu. Existují dvě předdefinované třídy, ze kterých můžete vytvořit objekty přepínač: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> třídy a <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> třídy. Můžete využít <xref:System.Diagnostics.BooleanSwitch> Pokud vám záleží pouze určuje, jestli se zobrazí zpráva trasování, použijete <xref:System.Diagnostics.TraceSwitch> Pokud chcete rozlišit úrovní trasování. Pokud používáte <xref:System.Diagnostics.TraceSwitch>, můžete definovat vlastní zprávy ladění a spojit je s různými úrovněmi trasování. Můžete použít oba typy přepínače trasování nebo ladění. Ve výchozím nastavení <xref:System.Diagnostics.BooleanSwitch> zakázána a <xref:System.Diagnostics.TraceSwitch> je nastavená na úroveň <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>. Přepínače trasování může být vytvořeno a umístí do libovolné části kódu, která může používat.  
  
 I když úrovní trasování a další možnosti konfigurace můžete nastavit v kódu, doporučujeme použít konfigurační soubor pro správu stavu vašich přepínače. Důvodem je, že správu konfigurace vašeho přepínače v konfigurační systém poskytuje větší flexibilitu, můžete zapnout nebo vypnout různé přepínače a měnit úrovně bez opětovné kompilace aplikace.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>Vytvoření a inicializace přepínačů trasování  
  
1. Definování přepínač jako buď typ <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> nebo typ <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> a nastavte název a popis přepínače.  
  
2. Nakonfigurujte přepínač trasování. Další informace najdete v tématu [konfigurace přepínačů trasování](#configure).  
  
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
 Poté, co vaše aplikace byla distribuována, můžete stále povolit nebo zakázat výstup trasování pomocí konfigurace přepínačů trasování ve vaší aplikaci. Konfigurace přepínače znamená, že změníte jeho hodnotu z externího zdroje, jakmile byla inicializována. Můžete změnit hodnoty přepínače objektů pomocí konfiguračního souboru. Při konfiguraci přepínače trasování můžete zapnout nebo vypnout, nebo k nastavení jeho úroveň určující velikost a typ zprávy ji předá do naslouchacích procesů.  
  
 Vaše přepínače jsou nakonfigurováni pomocí souboru .config. Pro webovou aplikaci Toto je soubor Web.config, který je přidružený k projektu. V aplikaci Windows, je tento soubor s názvem (název aplikace). exe.config. V nasazené aplikaci musí být tento soubor umístěn ve stejné složce jako spustitelný soubor.  
  
 Když vaše aplikace spustí kód, který vytvoří instanci přepínače poprvé, ověří konfigurační soubor pro úroveň trasování informace o pojmenovaných přepínači. Systém sledování zkontroluje konfigurační soubor jen jednou pro jakékoli konkrétní přepínač – poprvé aplikace vytváří přepínač.  
  
 V nasazení aplikace povolíte trasování kódu opětovná konfigurace přepínače objektů, pokud aplikace neběží. Obvykle to zahrnuje zapnutí přepínače objektů a vypnout nebo změnou úrovně trasování a následného restartování aplikace.  
  
 Při vytváření instance přepínače taky ji inicializovat zadáním dva argumenty: *displayName* argument a *popis* argument. *DisplayName* argument konstruktoru sady <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> vlastnost <xref:System.Diagnostics.Switch> instance třídy. *DisplayName* je název, který se používá ke konfiguraci přepínače v souboru .config a *popis* argument by měl vrátit stručný popis přepínač a co ho zprávy ovládací prvky.  
  
 Kromě zadání názvu přepínače ke konfiguraci, musíte zadat také hodnotu pro přepínač. Tato hodnota je celé číslo. Pro <xref:System.Diagnostics.BooleanSwitch>, hodnota 0 odpovídá **vypnout**, a odpovídá jakékoli nenulovou hodnotu **na**. Pro <xref:System.Diagnostics.TraceSwitch>0,1,2,3 a 4 odpovídají **vypnout**, **chyba**, **upozornění**, **informace**, a **Verbose**v uvedeném pořadí. Libovolné číslo větší než 4 je považován za **Verbose**a jakékoli číslo menší než nula je považován za **vypnout**.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 2.0 můžete zadat hodnotu pro přepínač text. Například `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo představující hodnotu výčtu, jako text `Error` pro <xref:System.Diagnostics.TraceSwitch>. Na řádku `<add name="myTraceSwitch" value="Error" />` je ekvivalentní `<add name="myTraceSwitch" value="1" />`.  
  
 Aby koncoví uživatelé moct konfigurace přepínačů trasování aplikace je nutné zadat podrobnou dokumentaci na přepínače ve vaší aplikaci. By měla podrobně popisují, které přepínače řídit, co a jak vypnout nebo zapnout. Koncový uživatel by měly také poskytnout soubor .config, který má odpovídající nápovědu v komentářích.  
  
#### <a name="to-configure-trace-switches"></a>Konfigurace přepínačů trasování  
  
1. Chcete-li použít přepínačů trasování, musíte je vytvořit a umístit je do kódu, jak je popsáno v části [vytváření a inicializace přepínačů trasování](#create).  
  
2. Pokud váš projekt neobsahuje soubor konfigurace (app.config nebo Web.config), pak z **projektu** nabídce vyberte možnost **přidat novou položku**.  
  
    -   **Visual Basic:** V **přidat novou položku** dialogového okna zvolte **konfiguračního souboru aplikace**.  
  
         Konfigurační soubor aplikace je vytvořen a otevřít. Toto je dokument XML, jejichž kořenový element `<configuration>.`  
  
    -   **Visual C#:** V **přidat novou položku** dialogového okna zvolte **soubor XML**. Název tohoto souboru **app.config**. Po deklaraci XML v editoru XML, přidejte následující kód XML:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Při kompilaci projektu souboru app.config je zkopírován do výstupní složky projektu a přejmenování *applicationname*. exe.config.  
  
3. Po `<configuration>` označit ale předtím, než `</configuration>` značky, přidejte odpovídající kód XML konfigurace vašeho přepínače. Následující příklady ukazují **BooleanSwitch** s **DisplayName** vlastnost `DataMessageSwitch` a **TraceSwitch** s **DisplayName**  vlastnost `TraceLevelSwitch`.  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     V této konfiguraci jak přepínače jsou vypnuté.  
  
4. Pokud je potřeba zapnout **BooleanSwitch**, jako `DataMessagesSwitch` je znázorněno v předchozím příkladu, změnit **hodnotu** libovolné celé číslo než 0.  
  
5. Pokud je potřeba zapnout **TraceSwitch**, jako `TraceLevelSwitch` je znázorněno v předchozím příkladu, změnit **hodnotu** úrovně (1 až 4) nastavení.  
  
6. Přidání komentářů do souboru .config, aby koncový uživatel má pochopili, jaké hodnoty chcete-li změnit konfiguraci přepínače odpovídajícím způsobem.  
  
     Následující příklad ukazuje, jak může vypadat konečný kód, komentáře, včetně:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [Trasování a ladění schématu nastavení](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
