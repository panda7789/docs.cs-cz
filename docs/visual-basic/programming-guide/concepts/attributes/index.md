---
title: "Přehled atributy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1d5399da42b224908fa9c23893eec5d424dd685
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="attributes-overview-visual-basic"></a>Přehled atributy (Visual Basic)
Atributy poskytují výkonný metoda spojování metadata nebo deklarativní informace s kódem (sestavení, typy, metody, vlastnosti a tak dále). Po atribut je spojen s entitou program, může být dotazován atribut v době běhu pomocí techniky názvem *reflexe*. Další informace najdete v tématu [reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
 Atributy mít následující vlastnosti:  
  
-   Atributy přidat metadata do programu. *Metadata* je informace o typech definované v programu. Všechny sestavení .NET obsahovat zadanou sadu metadata, která popisuje typy a členy typu definované v sestavení. Můžete přidat vlastní atributy pro žádné další informace, které jsou potřeba. Další informace najdete v tématu, [vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
-   Celý sestavení, moduly nebo menší program prvky, jako jsou například třídy a vlastnosti, můžete použít jeden nebo více atributů.  
  
-   Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.  
  
-   Váš program můžete zkontrolovat svůj vlastní metadata nebo metadata v ostatních aplikacích pomocí reflexe. Další informace najdete v tématu [přístup k atributy podle pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="using-attributes"></a>Pomocí atributů  
 Atributy je možné použít u libovolného deklarace, když konkrétní atribut může omezit přístup k deklarace, na kterých je platný. V jazyce Visual Basic je atribut uzavřené v lomených závorkách (\< >). Musí být uvedena bezprostředně před element, ke které se použije, na stejném řádku.  
  
 V tomto příkladu <xref:System.SerializableAttribute> atribut se používá k aplikování zvláštní vlastností pro třídu:  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 Metody s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarován takto:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 Více než jeden atribut je možné použít u deklaraci:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 Některé atributy lze zadat více než jednou pro danou entitu. Je například multiuse atribut <xref:System.Diagnostics.ConditionalAttribute>:  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  Podle konvence ukončete všechny názvy atributů slovem "Atribut" jej odlišit od jiných položek v rozhraní .NET Framework. Však není potřeba zadejte příponu atribut při použití atributů v kódu. Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, ale `DllImportAttribute` je skutečný název atributu v rozhraní .NET Framework.  
  
### <a name="attribute-parameters"></a>Atribut parametry  
 Počet atributů mít parametry, které může být poziční, nepojmenovaný nebo s názvem. Žádné poziční parametry musí být zadaný v určitém pořadí a nelze jej vynechat; pojmenované parametry jsou volitelné a lze jej zadat v libovolném pořadí. Nejprve jsou zadány poziční parametry. Například odpovídají tyto tři atributy:  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 První parametr název DLL je poziční a dodává se vždy první; ostatní s názvem. V takovém případě i s názvem výchozí parametry na hodnotu false, můžete vynechat. Vyhledejte jednotlivé atributy dokumentaci informace o výchozí hodnoty parametrů.  
  
### <a name="attribute-targets"></a>Cíle atributů  
 *Cíl* atributu je ta entita, na které se vztahuje atribut. Atribut může například použít třídu, konkrétní metody nebo celé sestavení. Ve výchozím nastavení atribut vztahuje k elementu, který ho předchází. Ale můžete také explicitně identifikovat, například zda atribut se použije na metodu, nebo její parametr nebo hodnoty.  
  
 K identifikaci explicitně atribut target, použijte následující syntaxi:  
  
```vb  
<target : attribute-list>  
```  
  
 Seznam možných `target` hodnoty je uvedené v následující tabulce.  
  
|Hodnota cíle|Platí pro|  
|------------------|----------------|  
|`assembly`|Celý sestavení|  
|`module`|Aktuální modul sestavení (který se liší od modulu jazyka Visual Basic)|  
  
 Následující příklad ukazuje, jak chcete použít atributy pro sestavení a moduly. Další informace najdete v tématu [běžné atributy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a>Běžná použití atributů  
 Následující seznam obsahuje několik příkladů běžných použití atributů v kódu:  
  
-   Označení metody pomocí `WebMethod` atribut v webové služby k označení, že metoda by měla být s přes protokol SOAP. Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.  
  
-   Popisující, jak při vzájemné spolupráci s nativním kódem zařazování parametry metody. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  
  
-   Popisující COM vlastnosti tříd, metod a rozhraní.  
  
-   Volání nespravovaného kódu pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> třídy.  
  
-   Která popisují vaše sestavení z hlediska název, verze, popis nebo ochranná známka.  
  
-   Popisující, kteří členové třídy k serializaci trvalosti.  
  
-   Popisující, jak pro mapování mezi členy třídy a z uzlů XML pro serializaci XML.  
  
-   Popisuje požadavky na zabezpečení pro metody.  
  
-   Zadání vlastnosti slouží k vynucení zabezpečení.  
  
-   Řízení optimalizace kompilátorem v běhu (JIT), takže stále snadno ladit kód.  
  
-   Získání informací o volajícího, aby metoda.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
-   [Vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [Postupy: vytváření sjednocení C/C++ pomocí atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [Mezi běžné atributy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [Informace o subjektu volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Atributy](https://msdn.microsoft.com/library/5x6cd29c)
