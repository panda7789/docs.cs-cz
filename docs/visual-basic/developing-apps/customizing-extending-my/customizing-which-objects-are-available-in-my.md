---
title: Přizpůsobení výběru objektů dostupných v oboru názvů My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: bb3f8eb2e8b1cf5bce364fc4b3ce0587769bb5f9
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775216"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Přizpůsobení výběru objektů dostupných v oboru názvů My (Visual Basic)

Toto téma popisuje, jak lze řídit, které `My` objekty jsou povoleny nastavením `_MYTYPE` konstanty podmíněné kompilace projektu. Integrované vývojové prostředí (IDE) sady Visual Studio udržuje `_MYTYPE` Konstanta podmíněné kompilace pro projekt v synchronizaci s typem projektu.  
  
## <a name="predefined-_mytype-values"></a>Předdefinované \_MYTYPE hodnoty  

K nastavení konstanty podmíněné kompilace `_MYTYPE` je nutné použít možnost kompilátoru `/define`. Při určení vlastní hodnoty pro `_MYTYPE` konstantu je nutné uzavřít řetězcovou hodnotu do sekvencí zpětného lomítka nebo uvozovky (\\). Můžete například použít:  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Tato tabulka ukazuje, co je Konstanta podmíněné kompilace `_MYTYPE` nastavena na pro několik typů projektů.  
  
|Typ projektu|hodnota \_MYTYPE|  
|------------------|--------------------|  
|Knihovna tříd|Systému|  
|Konzolová aplikace|Stromu|  
|Web|Webovém|  
|Knihovna webového ovládacího prvku|"WebControl"|  
|Aplikace systému Windows|WindowsForms|  
|Aplikace systému Windows, při které začíná vlastní `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Knihovna ovládacích prvků Windows|Systému|  
|Služba systému Windows|Stromu|  
|Obsahovat|Obsahovat|  
  
> [!NOTE]
> Všechna porovnání řetězců podmíněné kompilace rozlišují velká a malá písmena, bez ohledu na to, jak je příkaz `Option Compare` nastaven.  
  
## <a name="dependent-_my-compilation-constants"></a>Závislé konstanty kompilace \_MY  

@No__t_0 Konstanta podmíněné kompilace pak řídí hodnoty několika dalších konstant kompilace `_MY`:  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|Stromu|Stromu|Systému|Nedefinované|Systému|PODMÍNKA|  
|Uživatelská|Nedefinované|Nedefinované|Nedefinované|Nedefinované|Nedefinované|  
|Obsahovat|Nedefinované|Nedefinované|Nedefinované|Nedefinované|Nedefinované|  
|Webovém|Nedefinované|Webovém|CHYBNÉ|Webovém|CHYBNÉ|  
|"WebControl"|Nedefinované|Webovém|CHYBNÉ|Webovém|PODMÍNKA|  
|"Windows" nebo ""|Systému|Systému|Nedefinované|Systému|PODMÍNKA|  
|WindowsForms|WindowsForms|Systému|PODMÍNKA|Systému|PODMÍNKA|  
|"WindowsFormsWithCustomSubMain"|Stromu|Systému|PODMÍNKA|Systému|PODMÍNKA|  
  
 Ve výchozím nastavení jsou nedefinované konstanty podmíněné kompilace přeloženy na `FALSE`. Můžete zadat hodnoty pro nedefinované konstanty při kompilování projektu pro přepsání výchozího chování.  
  
> [!NOTE]
> Pokud je `_MYTYPE` nastaveno na "vlastní", projekt obsahuje `My` obor názvů, ale neobsahuje žádné objekty. Nicméně nastavení `_MYTYPE` na "Empty" brání kompilátoru v přidávání oboru názvů `My` a jeho objektů.  
  
 Tato tabulka popisuje vliv předdefinovaných hodnot konstant kompilace `_MY`.  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Povolí `My.Application`, pokud je konstanta "Console", "Windows" nebo "WindowsForms":<br /><br /> -Verze "Console" je odvozena z <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. a má méně členů než verze Windows.<br />– Verze "Windows" je odvozena z <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>. má méně členů než verze "WindowsForms".<br />– WindowsForms verze `My.Application` je odvozena od <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Pokud je `TARGET` konstanta definována jako "winexe", pak třída obsahuje metodu `Sub Main`.|  
|`_MYCOMPUTERTYPE`|Povolí `My.Computer`, pokud je konstanta "Web" nebo "Windows":<br /><br /> – Verze "Web" je odvozena z <xref:Microsoft.VisualBasic.Devices.ServerComputer> a má méně členů než verze Windows.<br />– Verze `My.Computer` Windows je odvozená od <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Povolí `My.Forms`, pokud je konstanta `TRUE`.|  
|`_MYUSERTYPE`|Povolí `My.User`, pokud je konstanta "Web" nebo "Windows":<br /><br /> – Webová verze `My.User` je přidružená k identitě uživatele aktuální žádosti HTTP.<br />– Verze `My.User` Windows je přidružená k aktuálnímu objektu zabezpečení vlákna.|  
|`_MYWEBSERVICES`|Povolí `My.WebServices`, pokud je konstanta `TRUE`.|  
|`_MYTYPE`|Povolí `My.Log`, `My.Request` a `My.Response`, pokud je konstanta "Web".|  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Závislost oboru názvů My na typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objekt My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
- [Objekt My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
- [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
