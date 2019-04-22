---
title: Přehled atributů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: bb012b49c76963306d723d7732b4c7054bf13ebb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827689"
---
# <a name="attributes-overview-visual-basic"></a>Přehled atributů (Visual Basic)
Atributy poskytují výkonný metoda spojování metadata nebo deklarativní informace s kódem (sestavení, typy, metody, vlastnosti a tak dále). Po atributu je spojen s entitou program, atribut může být dotázán za běhu pomocí techniky označované jako *reflexe*. Další informace najdete v tématu [reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
 Atributy mají následující vlastnosti:  
  
-   Atributy přidat metadata do programu. *Metadata* obsahuje informace o typy definované v programu. Všechna sestavení rozhraní .NET obsahují zadanou množinu metadata popisující typy a členy typu definované v sestavení. Můžete přidat vlastní atributy k jakékoli další informace, které je nutné zadat. Další informace najdete v tématu, [vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
-   Můžete použít jeden nebo více atributů na celé sestavení, moduly nebo menší prvky programu, jako například třídy a vlastnosti.  
  
-   Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.  
  
-   Aplikace můžete zkontrolovat svou vlastní metadaty nebo metadaty v jiných aplikacích pomocí reflexe. Další informace najdete v tématu [přístup k atributy podle použití reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="using-attributes"></a>Pomocí atributů  
 Atributy je možné použít u libovolného deklarace, když konkrétního atributu můžete narazit na omezení typů deklarace, na kterých je platný. V jazyce Visual Basic je atribut uzavřen do lomených závorek (\< >). Musí být bezprostředně před elementem, ke které se použije, na stejném řádku.  
  
 V tomto příkladu <xref:System.SerializableAttribute> atribut se používá k aplikování konkrétní charakteristiku pro třídu:  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 Metodu s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarován následujícím způsobem:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 Více než jeden atribut je možné použít v deklaraci:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 Některé atributy můžete zadat více než jednou pro danou entitu. Je například multiuse atribut <xref:System.Diagnostics.ConditionalAttribute>:  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  Podle konvence končí všechny názvy atributů slovem "Atribut", abychom je odlišili od ostatních položek v rozhraní .NET Framework. Ale není potřeba zadat atribut přípon při použití atributů v kódu. Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, ale `DllImportAttribute` je skutečný název atributu v rozhraní .NET Framework.  
  
### <a name="attribute-parameters"></a>Atribut parametrů  
 Mnoho atributů mít parametry, které mohou být poziční, nepojmenovaný nebo s názvem. Žádné poziční parametry musí být zadán v určitém pořadí a nelze jej vynechat; pojmenované parametry jsou volitelné a dá se zadat v libovolném pořadí. Poziční parametry jsou zadán jako první. Například tyto tři atributy jsou ekvivalentní:  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 První parametr, název knihovny DLL je poziční a dodává se vždycky první; ostatní jsou pojmenovány. V takovém případě pojmenované výchozí parametry na hodnotu false, takže lze vynechat. V dokumentaci jednotlivých atributů informace o výchozí hodnoty parametrů.  
  
### <a name="attribute-targets"></a>Cíle atributů  
 *Cílové* atributu je entita, ke kterému se vztahuje atribut. Atribut může například použít pro třídu, konkrétní metody nebo celé sestavení. Ve výchozím nastavení atribut se vztahuje k elementu, který předchází. Ale můžete také explicitně identifikovat, například zda atributu se použije k metodě, její parametr nebo na jeho návratovou hodnotu.  
  
 Cíl atributu explicitně identifikovat, použijte následující syntaxi:  
  
```vb  
<target : attribute-list>  
```  
  
 Seznam možných `target` hodnot je uveden v následující tabulce.  
  
|Cílová hodnota|Platí pro|  
|------------------|----------------|  
|`assembly`|Celé sestavení|  
|`module`|Aktuální modul sestavení (která se liší od modulu jazyka Visual Basic)|  
  
 Následující příklad ukazuje způsob použití atributů pro sestavení a modulů. Další informace najdete v tématu [běžné atributy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a>Běžné použití atributů  
 Následující seznam obsahuje několik běžných použití atributů v kódu:  
  
-   Označení metody pomocí `WebMethod` atribut ve webové služby k označení, že metoda mělo by být umožněno prostřednictvím protokolu SOAP. Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.  
  
-   Popis způsobu zařazení parametrů metody při vzájemné spolupráci s nativním kódem. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  
  
-   Popis vlastnosti modelu COM pro třídy, metody a rozhraní.  
  
-   Volání nespravovaného kódu pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> třídy.  
  
-   Popisující vaše sestavení z hlediska název, verze, popis nebo ochranná známka.  
  
-   Popisující, které členy třídy k serializaci trvalosti.  
  
-   Popisující způsob, jakým mapování mezi členy třídy a z uzlů XML pro serializaci kódu XML.  
  
-   Popisuje požadavky zabezpečení pro metody.  
  
-   Zadání vlastnosti používá k vynucení zabezpečení.  
  
-   Řízení optimalizace kompilátoru just-in-time (JIT), tak zůstane usnadňuje ladění kódu.  
  
-   Získání informací o volajícím metody.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
-   [Vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [Postupy: Vytváření sjednocení C/C++ pomocí atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [Běžné atributy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [Informace o volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atributy](../../../../standard/attributes/index.md)
