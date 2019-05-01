---
title: Přizpůsobení výběru objektů dostupných v oboru názvů My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: c0b47521c6a62071466ae4193cd8553bdfb3dcde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014229"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Přizpůsobení výběru objektů dostupných v oboru názvů My (Visual Basic)

Toto téma popisuje, jak můžete určit, které `My` objekty jsou povolené tak, že nastavíte váš projekt `_MYTYPE` – Konstanta podmíněné kompilace. Udržuje Visual Studio integrované vývojové prostředí (IDE) `_MYTYPE` – Konstanta podmíněné kompilace projektu synchronizované s typem projektu.  
  
## <a name="predefined-mytype-values"></a>Předdefinované \_MYTYPE hodnoty  

Je nutné použít `/define` – možnost kompilátoru nastavit `_MYTYPE` – Konstanta podmíněné kompilace. Když zadáte vlastní hodnoty `_MYTYPE` konstantní, musíte uzavřít řetězec hodnoty zpětné lomítko a znak uvozovek (\\") pořadí. Například můžete použít:  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Tato tabulka ukazuje, co `_MYTYPE` – Konstanta podmíněné kompilace nastaven pro několik typů projektů.  
  
|Typ projektu|\_Hodnota MYTYPE|  
|------------------|--------------------|  
|Knihovna tříd|"Windows"|  
|Konzolová aplikace|"Console"|  
|Web|"Web"|  
|Knihovna webových prvků|"WebControl."|  
|Aplikace Windows|"WindowsForms"|  
|Windows, pokud počínaje vlastní aplikace `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Knihovna ovládacích prvků Windows|"Windows"|  
|Služba systému Windows|"Console"|  
|prázdný|"Prázdný"|  
  
> [!NOTE]
> Veškeré porovnávání řetězců podmíněné kompilace jsou malá a velká písmena, bez ohledu na to, jak `Option Compare` příkaz nastavit.  
  
## <a name="dependent-my-compilation-constants"></a>Závislé \_Moje kompilace konstanty  

`_MYTYPE` – Konstanta podmíněné kompilace, pak určuje několik jiných hodnot `_MY` konstanty kompilace:  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Console"|"Console"|"Windows"|Nedefinováno|"Windows"|HODNOTA TRUE|  
|Možnost vlastní.|Nedefinováno|Nedefinováno|Nedefinováno|Nedefinováno|Nedefinováno|  
|"Prázdný"|Nedefinováno|Nedefinováno|Nedefinováno|Nedefinováno|Nedefinováno|  
|"Web"|Nedefinováno|"Web"|FALSE|"Web"|FALSE|  
|"WebControl."|Nedefinováno|"Web"|FALSE|"Web"|HODNOTA TRUE|  
|"Windows" nebo ""|"Windows"|"Windows"|Nedefinováno|"Windows"|HODNOTA TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|HODNOTA TRUE|"Windows"|HODNOTA TRUE|  
|"WindowsFormsWithCustomSubMain"|"Console"|"Windows"|HODNOTA TRUE|"Windows"|HODNOTA TRUE|  
  
 Ve výchozím nastavení, přeložit konstanty nedefinované podmíněné kompilace na `FALSE`. Při kompilaci projektu přepsat výchozí chování můžete zadat hodnoty pro konstanty nedefinovaný.  
  
> [!NOTE]
> Když `_MYTYPE` je nastavena na možnost vlastní"projekt obsahuje `My` obor názvů, ale neobsahuje žádné objekty. Však nastavení `_MYTYPE` na "Prázdný" zabrání kompilátoru přidání `My` obor názvů a jeho objektům.  
  
 Tato tabulka popisuje účinky předdefinované hodnoty `_MY` kompilace konstanty.  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Umožňuje `My.Application`, pokud je konstanta "Console" Windows, "nebo"WindowsForms":<br /><br /> – Verze "Console" je odvozen od <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. a nemá tolik členů než verze "Windows".<br />– Verze "Windows" je odvozen od <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>a má méně členů než verze "WindowsForms".<br />-"WindowsForms" verzi `My.Application` je odvozena z <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Pokud `TARGET` – konstanta je definován jako "winexe" pak obsahuje třídy `Sub Main` metoda.|  
|`_MYCOMPUTERTYPE`|Umožňuje `My.Computer`, pokud je konstanta "Www" nebo "Windows":<br /><br /> – Verze "Web" je odvozen od <xref:Microsoft.VisualBasic.Devices.ServerComputer>, a má méně členů než verze "Windows".<br />-"Windows" verzi `My.Computer` je odvozena z <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Umožňuje `My.Forms`, pokud je konstanta `TRUE`.|  
|`_MYUSERTYPE`|Umožňuje `My.User`, pokud je konstanta "Www" nebo "Windows":<br /><br /> – "Webová" verze `My.User` souvisí s uživatelskou identitu pro aktuální žádost HTTP.<br />-"Windows" verzi `My.User` je přidružený aktuální objekt zabezpečení vlákna.|  
|`_MYWEBSERVICES`|Umožňuje `My.WebServices`, pokud je konstanta `TRUE`.|  
|`_MYTYPE`|Umožňuje `My.Log`, `My.Request`, a `My.Response`, pokud je konstanta "Web".|  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Závislost oboru názvů My na typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objekt My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
- [Objekt My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
- [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
