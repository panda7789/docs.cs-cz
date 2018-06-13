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
ms.openlocfilehash: 4088c74d0ea8e9f2ad70aff37d99870d34b168ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392928"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Postupy: Vytváření, inicializace a konfigurace přepínačů trasování
Trasování – přepínače umožňují povolit, zakázat a filtrovat výstup trasování.  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a>Vytváření a inicializace přepínače trasování  
 Chcete-li použít trasování – přepínače, musíte nejprve je vytvořte a umístěte je do vašeho kódu. Existují dvě předdefinované třídy, ze kterých můžete vytvořit objekty přepínač: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> třídy a <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> třídy. Byste použili <xref:System.Diagnostics.BooleanSwitch> Pokud se zajímáte pouze o tom, zda se zobrazí zpráva trasování; byste použili <xref:System.Diagnostics.TraceSwitch> Pokud chcete rozlišit úrovně trasování. Pokud používáte <xref:System.Diagnostics.TraceSwitch>, můžete definovat vlastní zprávy ladění a přidružit úrovně různých trasování. Můžete vytvořit oba typy přepínačů trasování nebo ladění. Ve výchozím nastavení <xref:System.Diagnostics.BooleanSwitch> je zakázána a <xref:System.Diagnostics.TraceSwitch> je nastavena úroveň <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>. Trasování – přepínače můžete vytvořit a uložena v žádné části kódu, může je použít.  
  
 I když v kódu můžete nastavit úrovně trasování a další možnosti konfigurace, doporučujeme vám, použijte konfigurační soubor pro správu stavu vaší přepínače. Důvodem je, že správa konfigurace vaší přepínačů v konfigurační systém vám dává větší flexibilitu – můžete zapnout a vypnout různé přepínače a změnit úrovně bez nutnosti rekompilace vaší aplikace.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>K vytvoření a inicializace přepínače trasování  
  
1.  Zadejte přepínač jako buď typ <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> nebo typ <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> a nastavte název a popis přepínače.  
  
2.  Nakonfigurujte přepínač trasování. Další informace najdete v tématu [Konfigurace trasování – přepínače](#configure).  
  
     Následující kód vytvoří dva přepínače, každého typu:  
  
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
## <a name="configuring-trace-switches"></a>Konfigurace trasování – přepínače  
 Poté, co byla distribuována aplikace, můžete stále povolíte nebo zakážete výstup trasování pomocí konfigurace přepínačů trasování ve vaší aplikaci. Konfigurace portu přepínače znamená změna svou hodnotu z externího zdroje po byl inicializován. Můžete změnit hodnoty přepínače objektů pomocí konfiguračního souboru. Nakonfigurujte přepínač trasování ji zapnout a vypnout, nebo jeho úroveň určení velikost a typ zprávy se předá podél naslouchací procesy.  
  
 Vaše přepínače jsou nakonfigurované pomocí souboru .config. Pro webovou aplikaci Toto je soubor Web.config přidružený k projektu. V aplikaci Windows, je tento soubor s názvem (název aplikace). exe.config. V nasazení aplikace musí být tento soubor umístěn ve stejné složce jako spustitelný soubor.  
  
 Když aplikaci spustí kód, který vytvoří instanci přepínače poprvé, zkontroluje konfiguračního souboru pro úroveň trasování informace o pojmenované přepínači. Systém trasování hodnotu konfigurační soubor jenom jednou pro všechny konkrétní přepínač – poprvé vytváří vaše aplikace přepínač.  
  
 V nasazení aplikace povolíte kód trasování překonfigurování přepínače objektů, pokud aplikace není spuštěna. Obvykle to zahrnuje zapnutí přepínače objektů a vypnout nebo změnou úrovně trasování a následné restartování aplikace.  
  
 Při vytváření instance přepínače, můžete také provést jeho inicializaci zadáním dva argumenty: *displayName* argument a *popis* argument. *DisplayName* argument konstruktoru sad <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> vlastnost <xref:System.Diagnostics.Switch> instance třídy. *DisplayName* je název, který slouží ke konfiguraci přepínače v souboru config a *popis* argument by měla vrátit stručný popis přepínač a co ho zprávy ovládací prvky.  
  
 Kromě určení názvu přepínače ke konfiguraci, musíte zadat také hodnotu pro přepínač. Tato hodnota je celé číslo. Pro <xref:System.Diagnostics.BooleanSwitch>, hodnota 0 odpovídá **vypnout**, a jakákoliv nenulová hodnota odpovídá **na**. Pro <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3 a 4 odpovídají **vypnout**, **chyba**, **upozornění**, **informace**, a **podrobné**, v uvedeném pořadí. Žádné číslo větší než 4 je považován za **podrobné**a všechny číslo menší než nula je považován za **vypnout**.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 2.0 můžete zadat hodnotu pro přepínač text. Například `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo text, například představující hodnotu výčtu `Error` pro <xref:System.Diagnostics.TraceSwitch>. Na řádku `<add name="myTraceSwitch" value="Error" />` je ekvivalentní `<add name="myTraceSwitch" value="1" />`.  
  
 Aby koncoví uživatelé moct konfigurace přepínačů trasování aplikace je nutné zadat podrobnou dokumentaci v přepínačích v aplikaci. Měli podrobnosti, které přepínače řídit, co a jak vypnout nebo zapnout. Koncový uživatel musí poskytnout i soubor .config, který má odpovídající nápovědu v komentářích.  
  
#### <a name="to-configure-trace-switches"></a>Konfigurace trasování – přepínače  
  
1.  Chcete-li použít trasování – přepínače, musíte nejprve je vytvořte a umístěte je do vašeho kódu, jak je popsáno v části [vytváření a inicializace přepínače trasování](#create).  
  
2.  Pokud projekt neobsahuje soubor konfigurace (app.config nebo Web.config), pak z **projektu** nabídce vyberte možnost **přidat novou položku**.  
  
    -   **Visual Basic:** v **přidat novou položku** dialogovém okně vyberte **konfigurační soubor aplikace**.  
  
         Konfigurační soubor aplikace je vytvořen a otevřít. Toto je dokument XML, jehož kořenový element `<configuration>.`  
  
    -   **Visual C#:** v **přidat novou položku** dialogovém okně vyberte **souboru XML**. Název tohoto souboru **app.config**. V editoru XML po deklaraci XML, přidejte následující kód XML:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Při kompilaci projektu soubor app.config se zkopíruje do zadané výstupní složce projektu a přejmenován *applicationname*. exe.config.  
  
3.  Po `<configuration>` značky, ale předtím, než `</configuration>` značka, přidejte příslušný soubor XML konfigurace vaší přepínače. Následující příklady ukazují **BooleanSwitch** s **DisplayName** vlastnost `DataMessageSwitch` a **TraceSwitch** s **DisplayName**  vlastnost `TraceLevelSwitch`.  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     V této konfiguraci oba přepínače jsou vypnuté.  
  
4.  Pokud budete muset zapnout **BooleanSwitch**, jako například `DataMessagesSwitch` ukazuje předchozí příklad, změnit **hodnotu** libovolné celé číslo než 0.  
  
5.  Pokud budete muset zapnout **TraceSwitch**, například `TraceLevelSwitch` ukazuje předchozí příklad, změnit **hodnotu** na příslušné úrovni nastavení (1 až 4).  
  
6.  Přidání komentářů do souboru .config, aby koncový uživatel měli vědět, jaké hodnoty chcete-li změnit správně nakonfigurovat přepínače.  
  
     Následující příklad ukazuje, jak může vypadat poslední kód, včetně komentář:  
  
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
 [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [Trasování a ladění schématu nastavení](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
