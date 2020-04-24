---
title: Přizpůsobení výběru objektů dostupných v oboru názvů My
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: 0387aca08e3a31b0a2045369919894d88caf5b76
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330313"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Přizpůsobení výběru objektů dostupných v oboru názvů My (Visual Basic)

Toto téma popisuje, jak lze řídit, `My` které objekty jsou povoleny, nastavením konstanty `_MYTYPE` podmíněné kompilace vašeho projektu. Integrované vývojové prostředí (IDE) sady Visual Studio udržuje konstantu `_MYTYPE` podmíněné kompilace pro projekt v synchronizaci s typem projektu.  
  
## <a name="predefined-_mytype-values"></a>Předdefinované \_hodnoty MyType  

K nastavení konstanty `/define` `_MYTYPE` podmíněné kompilace je nutné použít možnost kompilátoru. Při zadávání vlastní hodnoty pro `_MYTYPE` konstantu je nutné uzavřít řetězcovou hodnotu do sekvencí zpětného lomítka nebo uvozovky\\("). Můžete například použít:  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Tato tabulka ukazuje, `_MYTYPE` co je Konstanta podmíněné kompilace nastavena na pro několik typů projektů.  
  
|Typ projektu|\_Hodnota MYTYPE|  
|------------------|--------------------|  
|Knihovna tříd|Systému|  
|Konzolová aplikace|Stromu|  
|Web|Webovém|  
|Knihovna webového ovládacího prvku|"WebControl"|  
|Aplikace systému Windows|WindowsForms|  
|Aplikace systému Windows, při zahájení s vlastním`Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Knihovna ovládacích prvků Windows|Systému|  
|Služba systému Windows|Stromu|  
|Obsahovat|Obsahovat|  
  
> [!NOTE]
> Všechna porovnání řetězců podmíněné kompilace rozlišují velká a malá písmena, bez ohledu na to, `Option Compare` jak je příkaz nastaven.  
  
## <a name="dependent-_my-compilation-constants"></a>Závislé \_konstanty kompilace  

Konstanta `_MYTYPE` podmíněné kompilace pak řídí hodnoty několika dalších `_MY` konstant kompilace:  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|Stromu|Stromu|Systému|Nedefinované|Systému|TRUE|  
|Uživatelská|Nedefinované|Nedefinované|Nedefinované|Nedefinované|Nedefinované|  
|Obsahovat|Nedefinované|Nedefinované|Nedefinované|Nedefinované|Nedefinované|  
|Webovém|Nedefinované|Webovém|FALSE|Webovém|FALSE|  
|"WebControl"|Nedefinované|Webovém|FALSE|Webovém|TRUE|  
|"Windows" nebo ""|Systému|Systému|Nedefinované|Systému|TRUE|  
|WindowsForms|WindowsForms|Systému|TRUE|Systému|TRUE|  
|"WindowsFormsWithCustomSubMain"|Stromu|Systému|TRUE|Systému|TRUE|  
  
 Ve výchozím nastavení jsou nedefinované konstanty podmíněné kompilace přehodnoceny na `FALSE`. Můžete zadat hodnoty pro nedefinované konstanty při kompilování projektu pro přepsání výchozího chování.  
  
> [!NOTE]
> Když `_MYTYPE` je nastavená na Custom (vlastní), projekt obsahuje `My` obor názvů, ale neobsahuje žádné objekty. Nastavení `_MYTYPE` na "prázdné" však brání kompilátoru v přidání `My` oboru názvů a jeho objektů.  
  
 Tato tabulka popisuje účinky předdefinovaných hodnot konstant `_MY` kompilace.  
  
|Trvalé|Význam|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Povolí `My.Application`, pokud je konstanta "Console", "Windows" nebo "WindowsForms":<br /><br /> -Verze "Console" je odvozena z <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. a má méně členů než verze Windows.<br />– Verze "Windows" je odvozena z <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>. a má méně členů než verze "WindowsForms".<br />– Verze "WindowsForms" `My.Application` je odvozena z. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Je- `TARGET` li konstanta definována jako "winexe", pak třída obsahuje `Sub Main` metodu.|  
|`_MYCOMPUTERTYPE`|Povolí `My.Computer`, pokud je konstanta "Web" nebo "Windows":<br /><br /> – Verze "Web" je odvozena z <xref:Microsoft.VisualBasic.Devices.ServerComputer>a má méně členů než verze Windows.<br />-Verze "Windows" `My.Computer` je odvozena z. <xref:Microsoft.VisualBasic.Devices.Computer>|  
|`_MYFORMS`|Povolí `My.Forms`, pokud je `TRUE`konstanta.|  
|`_MYUSERTYPE`|Povolí `My.User`, pokud je konstanta "Web" nebo "Windows":<br /><br /> -Verze "Web" `My.User` je přidružena k identitě uživatele aktuální žádosti HTTP.<br />-Verze "Windows" `My.User` je přidružena k aktuálnímu objektu zabezpečení vlákna.|  
|`_MYWEBSERVICES`|Povolí `My.WebServices`, pokud je `TRUE`konstanta.|  
|`_MYTYPE`|Povolí `My.Log`, `My.Request`a `My.Response`, pokud je konstanta "Web".|  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Závislost oboru názvů My na typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms – objekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objekt My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response – objekt](../../../visual-basic/language-reference/objects/my-response-object.md)
- [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
