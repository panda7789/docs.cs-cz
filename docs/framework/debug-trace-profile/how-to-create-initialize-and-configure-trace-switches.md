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
ms.openlocfilehash: 358e34b2ce5d896ba02b343ce060604f2d42eeeb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216478"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Postupy: Vytváření, inicializace a konfigurace přepínačů trasování
Přepínače trasování umožňují povolit, zakázat a filtrovat výstup trasování.  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a>Vytvoření a inicializace přepínače trasování  
 Aby bylo možné použít přepínače trasování, je nutné je nejprve vytvořit a umístit do kódu. Existují dvě předdefinované třídy, ze kterých lze vytvořit objekty Switch: třídu <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> a třídu <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>. Pokud se chcete zajímat jenom o tom, jestli se zobrazuje zpráva o trasování, použijte <xref:System.Diagnostics.BooleanSwitch>. Pokud chcete odlišit úrovně trasování, použijte <xref:System.Diagnostics.TraceSwitch>. Pokud používáte <xref:System.Diagnostics.TraceSwitch>, můžete definovat vlastní zprávy pro ladění a přidružit je k různým úrovním trasování. Oba typy přepínačů lze použít buď pomocí trasování, nebo ladění. Ve výchozím nastavení je <xref:System.Diagnostics.BooleanSwitch> zakázaný a <xref:System.Diagnostics.TraceSwitch> je nastavená na úroveň <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>. Přepínače trasování lze vytvořit a umístit do jakékoli části kódu, který je může používat.  
  
 I když můžete nastavit úrovně trasování a další možnosti konfigurace v kódu, doporučujeme, abyste ke správě stavu přepínačů použili konfigurační soubor. Důvodem je to, že Správa konfigurace přepínačů v konfiguračním systému poskytuje větší flexibilitu – můžete zapnout a vypnout různé přepínače a změnit úrovně bez nutnosti opětovné kompilace aplikace.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>Chcete-li vytvořit a inicializovat přepínač trasování  
  
1. Definujte přepínač buď jako typ <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType>, nebo zadejte <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> a nastavte název a popis přepínače.  
  
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
 Po distribuci aplikace můžete povolit nebo zakázat výstup trasování konfigurací přepínačů trasování v aplikaci. Konfigurace přepínače znamená změnu hodnoty z externího zdroje poté, co byla inicializována. Hodnoty objektů Switch můžete změnit pomocí konfiguračního souboru. Můžete nakonfigurovat přepínač trasování pro jeho zapnutí a vypnutí nebo pro nastavení jeho úrovně a určení množství a typu zpráv, které předává do posluchačů.  
  
 Vaše přepínače jsou nakonfigurovány pomocí souboru. config. Pro webovou aplikaci je to soubor Web. config přidružený k projektu. V aplikaci pro Windows se tento soubor nazývá (název aplikace). exe. config. V nasazené aplikaci musí být tento soubor umístěn ve stejné složce jako spustitelný soubor.  
  
 Když vaše aplikace spustí kód, který vytvoří instanci přepínače poprvé, zkontroluje konfigurační soubor o informace na úrovni trasování s pojmenovaným přepínačem. Systém trasování prověřuje konfigurační soubor pouze jednou pro konkrétní přepínač – při prvním vytvoření přepínače aplikace.  
  
 V nasazené aplikaci povolíte trasovací kód tím, že překonfigurujete objekty přepínače, když vaše aplikace neběží. To obvykle zahrnuje zapnutí a vypnutí objektů přepínače nebo změnu úrovní trasování a následné restartování aplikace.  
  
 Když vytvoříte instanci přepínače, inicializujete ji také zadáním dvou argumentů: argumentu *DisplayName* a argumentem *Description* . Argument *DisplayName* konstruktoru nastavuje vlastnost <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> instance <xref:System.Diagnostics.Switch> třídy. *DisplayName* je název, který se používá ke konfiguraci přepínače v souboru. config a argument *Description* by měl vracet stručný popis přepínače a o tom, které zprávy ovládací prvky IT.  
  
 Kromě určení názvu přepínače, který se má nakonfigurovat, musíte zadat také hodnotu pro přepínač. Tato hodnota je celé číslo. Pro <xref:System.Diagnostics.BooleanSwitch>hodnota 0 odpovídá **off**a jakákoli nenulová hodnota odpovídá **na**. U <xref:System.Diagnostics.TraceSwitch>, 0, 1, 2, 3 a **4, v uvedeném pořadí odpovídá** **Chyba**, **Upozornění**, **informace**a **podrobné**. Jakékoli číslo, které je větší než 4, je považováno za **podrobné**a jakékoli číslo menší než nula je považováno za **vypnuto**.  
  
> [!NOTE]
> V .NET Framework verze 2,0 můžete použít text a zadat hodnotu pro přepínač. Například `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo text představující hodnotu výčtu, jako je například `Error` pro <xref:System.Diagnostics.TraceSwitch>. `<add name="myTraceSwitch" value="Error" />` řádku je ekvivalentem `<add name="myTraceSwitch" value="1" />`.  
  
 Aby koncoví uživatelé mohli konfigurovat přepínače trasování aplikace, musíte poskytnout podrobnou dokumentaci k přepínačům ve vaší aplikaci. Měli byste si podrobně udělat, které přepínače řídí, co a jak je zapnout nebo vypnout. Měli byste také poskytnout koncovému uživateli soubor. config, který má v komentářích odpovídající nápovědě.  
  
#### <a name="to-configure-trace-switches"></a>Konfigurace přepínačů trasování  
  
1. Aby bylo možné použít přepínače trasování, je nutné je nejprve vytvořit a umístit do kódu, jak je popsáno v části [Vytvoření a inicializace přepínače trasování](#create).  
  
2. Pokud projekt neobsahuje konfigurační soubor (App. config nebo Web. config), pak v nabídce **projekt** vyberte možnost **Přidat novou položku**.  
  
    - **Visual Basic:** V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.  
  
         Konfigurační soubor aplikace je vytvořen a otevřen. Toto je dokument XML, jehož kořenový element je `<configuration>.`  
  
    - **Vizuál C#:** v dialogovém okně **Přidat novou položku** vyberte **soubor XML**. Pojmenujte tento soubor **App. config**. V editoru XML po deklaraci XML přidejte následující kód XML:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Při kompilaci projektu se soubor App. config zkopíruje do výstupní složky projektu a přejmenuje se na soubor *ApplicationName*. exe. config.  
  
3. Po značce `<configuration>`, ale před značkou `</configuration>`, přidejte odpovídající XML pro konfiguraci přepínačů. Následující příklady ukazují **BooleanSwitch** s vlastností **DisplayName** `DataMessageSwitch` a **TraceSwitch** s vlastností **DisplayName** `TraceLevelSwitch`.  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     V této konfiguraci jsou oba přepínače vypnuté.  
  
4. Pokud potřebujete zapnout **BooleanSwitch**, například `DataMessagesSwitch` znázorněné v předchozím příkladu, změňte **hodnotu** na celé číslo jiné než 0.  
  
5. Pokud potřebujete zapnout **TraceSwitch**, jako je například `TraceLevelSwitch` znázorněné v předchozím příkladu, změňte **hodnotu** na nastavení odpovídající úrovně (1 až 4).  
  
6. Přidejte komentáře do souboru. config tak, aby měl koncový uživatel jasné porozumění hodnotám, které se mají změnit, a odpovídajícím způsobem nakonfigurovat přepínače.  
  
     Následující příklad ukazuje, jak může vypadat konečný kód včetně komentářů.  
  
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
