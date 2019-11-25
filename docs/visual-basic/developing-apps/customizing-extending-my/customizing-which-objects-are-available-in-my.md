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

This topic describes how you can control which `My` objects are enabled by setting your project's `_MYTYPE` conditional-compilation constant. The Visual Studio Integrated Development Environment (IDE) keeps the `_MYTYPE` conditional-compilation constant for a project in sync with the project's type.  
  
## <a name="predefined-_mytype-values"></a>Predefined \_MYTYPE Values  

You must use the `/define` compiler option to set the `_MYTYPE` conditional-compilation constant. When specifying your own value for the `_MYTYPE` constant, you must enclose the string value in backslash/quotation mark (\\") sequences. For example, you could use:  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 This table shows what the `_MYTYPE` conditional-compilation constant is set to for several project types.  
  
|Project type|\_MYTYPE value|  
|------------------|--------------------|  
|Knihovna tříd|"Windows"|  
|Konzolová aplikace|"Console"|  
|Web|"Web"|  
|Web Control Library|"WebControl"|  
|Windows Application|"WindowsForms"|  
|Windows Application, when starting with custom `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Windows Control Library|"Windows"|  
|Služba systému Windows|"Console"|  
|Empty|"Empty"|  
  
> [!NOTE]
> All conditional-compilation string comparisons are case-sensitive, regardless of how the `Option Compare` statement is set.  
  
## <a name="dependent-_my-compilation-constants"></a>Dependent \_MY Compilation Constants  

The `_MYTYPE` conditional-compilation constant, in turn, controls the values of several other `_MY` compilation constants:  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Console"|"Console"|"Windows"|Undefined|"Windows"|TRUE|  
|"Custom"|Undefined|Undefined|Undefined|Undefined|Undefined|  
|"Empty"|Undefined|Undefined|Undefined|Undefined|Undefined|  
|"Web"|Undefined|"Web"|FALSE|"Web"|FALSE|  
|"WebControl"|Undefined|"Web"|FALSE|"Web"|TRUE|  
|"Windows" or ""|"Windows"|"Windows"|Undefined|"Windows"|TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|TRUE|"Windows"|TRUE|  
|"WindowsFormsWithCustomSubMain"|"Console"|"Windows"|TRUE|"Windows"|TRUE|  
  
 By default, undefined conditional-compilation constants resolve to `FALSE`. You can specify values for the undefined constants when compiling your project to override the default behavior.  
  
> [!NOTE]
> When `_MYTYPE` is set to "Custom", the project contains the `My` namespace, but it contains no objects. However, setting `_MYTYPE` to "Empty" prevents the compiler from adding the `My` namespace and its objects.  
  
 This table describes the effects of the predefined values of the `_MY` compilation constants.  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Enables `My.Application`, if the constant is "Console," Windows," or "WindowsForms":<br /><br /> -   The "Console" version derives from <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. and has fewer members than the "Windows" version.<br />-   The "Windows" version derives from <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>.and has fewer members than the "WindowsForms" version.<br />-   The "WindowsForms" version of `My.Application` derives from <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. If the `TARGET` constant is defined to be "winexe", then the class includes a `Sub Main` method.|  
|`_MYCOMPUTERTYPE`|Enables `My.Computer`, if the constant is "Web" or "Windows":<br /><br /> -   The "Web" version derives from <xref:Microsoft.VisualBasic.Devices.ServerComputer>, and has fewer members than the "Windows" version.<br />-   The "Windows" version of `My.Computer` derives from <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Enables `My.Forms`, if the constant is `TRUE`.|  
|`_MYUSERTYPE`|Enables `My.User`, if the constant is "Web" or "Windows":<br /><br /> -   The "Web" version of `My.User` is associated with the user identity of the current HTTP request.<br />-   The "Windows" version of `My.User` is associated with the thread's current principal.|  
|`_MYWEBSERVICES`|Enables `My.WebServices`, if the constant is `TRUE`.|  
|`_MYTYPE`|Enables `My.Log`, `My.Request`, and `My.Response`, if the constant is "Web".|  
  
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
