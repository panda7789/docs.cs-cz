---
title: Přizpůsobení výběru objektů dostupných v oboru názvů My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: caddad463f7c525c8b715d70f49bf8bebcc7cfbd
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701255"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Přizpůsobení výběru objektů dostupných v oboru názvů My (Visual Basic)

Toto téma popisuje, jak lze řídit, které objekty `My` jsou povoleny nastavením konstanty podmíněné kompilace `_MYTYPE` projektu. Integrované vývojové prostředí (IDE) sady Visual Studio udržuje pro projekt v synchronizaci s typem projektu konstantu podmíněné kompilace `_MYTYPE`.  
  
## <a name="predefined-_mytype-values"></a>Předdefinované hodnoty @no__t – 0MYTYPE  

Chcete-li nastavit konstantu podmíněné kompilace `_MYTYPE`, je nutné použít možnost kompilátoru `/define`. Při zadávání vlastní hodnoty pro konstantu `_MYTYPE` je nutné uzavřít řetězcovou hodnotu do sekvencí zpětného lomítka nebo uvozovky (\\ "). Můžete například použít:  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Tato tabulka ukazuje, co je Konstanta podmíněné kompilace `_MYTYPE` nastavená na pro několik typů projektů.  
  
|Typ projektu|@no__t – hodnota 0MYTYPE|  
|------------------|--------------------|  
|Knihovna tříd|Systému|  
|Konzolová aplikace|Stromu|  
|Web|Webovém|  
|Knihovna webového ovládacího prvku|"WebControl"|  
|Aplikace systému Windows|WindowsForms|  
|Aplikace systému Windows, při zahájení vlastního `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Knihovna ovládacích prvků Windows|Systému|  
|Služba systému Windows|Stromu|  
|Obsahovat|Obsahovat|  
  
> [!NOTE]
> Všechna porovnání řetězců podmíněné kompilace rozlišují velká a malá písmena, bez ohledu na to, jak je nastaven příkaz `Option Compare`.  
  
## <a name="dependent-_my-compilation-constants"></a>Závislé konstanty kompilace @no__t – 0MY  

Konstanta podmíněné kompilace `_MYTYPE` určuje hodnoty několika dalších konstant kompilace `_MY`:  
  
|@no__t – 0MYTYPE|@no__t – 0MYAPPLICATIONTYPE|@no__t – 0MYCOMPUTERTYPE|@no__t – 0MYFORMS|@no__t – 0MYUSERTYPE|@no__t – 0MYWEBSERVICES|  
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
> Pokud je `_MYTYPE` nastavená na "vlastní", projekt obsahuje obor názvů `My`, ale neobsahuje žádné objekty. Nastavení `_MYTYPE` na "prázdné" však brání kompilátoru v přidání oboru názvů `My` a jeho objektů.  
  
 Tato tabulka popisuje účinky předdefinovaných hodnot konstant kompilace `_MY`.  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Povolí `My.Application`, pokud je konstanta "Console", "Windows" nebo "WindowsForms":<br /><br /> -Verze "Console" je odvozena z <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. a má méně členů než verze Windows.<br />– Verze "Windows" je odvozena z @no__t -0 a má méně členů než verze "WindowsForms".<br />– WindowsForms verze `My.Application` je odvozena z <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Pokud je konstanta `TARGET` definována jako "winexe", pak třída obsahuje metodu `Sub Main`.|  
|`_MYCOMPUTERTYPE`|Povolí `My.Computer`, pokud je konstanta "Web" nebo "Windows":<br /><br /> – Verze "Web" je odvozena z <xref:Microsoft.VisualBasic.Devices.ServerComputer> a má méně členů než verze Windows.<br />– Verze "Windows" `My.Computer` je odvozena z <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Povolí `My.Forms`, pokud je konstanta `TRUE`.|  
|`_MYUSERTYPE`|Povolí `My.User`, pokud je konstanta "Web" nebo "Windows":<br /><br /> – Verze "Web" `My.User` je přidružená k identitě uživatele aktuální žádosti HTTP.<br />– Verze "Windows" `My.User` je přidružena k aktuálnímu objektu zabezpečení vlákna.|  
|`_MYWEBSERVICES`|Povolí `My.WebServices`, pokud je konstanta `TRUE`.|  
|`_MYTYPE`|Povolí `My.Log`, `My.Request` a `My.Response`, pokud je konstanta "Web".|  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Závislost oboru názvů My na typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objekt My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
- [Objekt My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
- [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
