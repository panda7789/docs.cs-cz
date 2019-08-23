---
title: Přehled atributů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: c799b9be9b936beadde28374bd9882ebc6e2d9a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966322"
---
# <a name="attributes-overview-visual-basic"></a>Přehled atributů (Visual Basic)
Atributy poskytují výkonnou metodu přidružování metadat nebo deklarativní informace, s kódem (sestavení, typy, metodami, vlastnostmi a tak dále). Po přiřazení atributu k entitě programu lze pomocí metody s názvem reflexe zadat dotaz na atribut v době běhu. Další informace naleznete v tématu [reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
 Atributy mají následující vlastnosti:  
  
- Atributy přidávají do programu metadata. *Metadata* jsou informace o typech definovaných v programu. Všechna sestavení .NET obsahují zadanou sadu metadat, které popisují typy a členy typu definované v sestavení. Můžete přidat vlastní atributy a zadat případné další požadované informace. Další informace najdete v tématu [Vytvoření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
- Jeden nebo více atributů lze použít pro celá sestavení, moduly nebo menší prvky programu, jako jsou třídy a vlastnosti.  
  
- Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.  
  
- Váš program může prošetřit vlastní metadata nebo metadata v jiných programech pomocí reflexe. Další informace naleznete v tématu [přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="using-attributes"></a>Používání atributů  
 Atributy lze umístit na většinu jakékoli deklarace, i když konkrétní atribut může omezit typy deklarací, na kterých je platný. V Visual Basic je atribut uzavřený v lomených závorkách\< (>). Musí se objevit bezprostředně před prvkem, na který je použit, na stejném řádku.  
  
 V tomto příkladu <xref:System.SerializableAttribute> je atribut použit k použití konkrétní charakteristiky pro třídu:  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 Metoda s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarována takto:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 V deklaraci lze umístit více než jeden atribut:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 Některé atributy lze pro danou entitu zadat více než jednou. Příklad takového atributu Multiuse je <xref:System.Diagnostics.ConditionalAttribute>:  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
> Podle konvence názvy všech atributů končí slovem "Attribute", aby je bylo možné odlišit od ostatních položek v .NET Framework. Při použití atributů v kódu však není nutné zadávat příponu atributu. Například `[DllImport]` je ekvivalentní k `[DllImportAttribute]`, ale `DllImportAttribute` je skutečným názvem atributu v .NET Framework.  
  
### <a name="attribute-parameters"></a>Parametry atributu  
 Mnoho atributů má parametry, které mohou být pozice, nepojmenované nebo pojmenované. V určitém pořadí musí být zadány všechny poziční parametry a nelze je vynechat; pojmenované parametry jsou volitelné a lze je zadat v libovolném pořadí. Poziční parametry jsou uvedeny jako první. Například tyto tři atributy jsou ekvivalentní:  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 První parametr, název knihovny DLL, je pozice a vždy se nachází jako první; ostatní mají název. V takovém případě mají obě pojmenované parametry výchozí hodnotu false, takže je lze vynechat. Informace o výchozích hodnotách parametrů naleznete v dokumentaci k jednotlivým atributům.  
  
### <a name="attribute-targets"></a>Cíle atributů  
 *Cíl* atributu je entita, na kterou se atribut vztahuje. Atribut může například platit pro třídu, konkrétní metodu nebo celé sestavení. Ve výchozím nastavení se atribut vztahuje na element, který předchází. Můžete ale také explicitně určit, zda je atribut použit na metodu, nebo na jeho parametr nebo na jeho návratovou hodnotu.  
  
 K explicitní identifikaci cíle atributu použijte následující syntaxi:  
  
```vb  
<target : attribute-list>  
```  
  
 Seznam možných `target` hodnot je uveden v následující tabulce.  
  
|Cílová hodnota|Platí pro|  
|------------------|----------------|  
|`assembly`|Celé sestavení|  
|`module`|Aktuální modul sestavení (který se liší od modulu Visual Basic)|  
  
 Následující příklad ukazuje, jak použít atributy na sestavení a moduly. Další informace najdete v tématu [běžné atributy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a>Běžné použití atributů  
 Následující seznam obsahuje několik běžných použití atributů v kódu:  
  
- Označení metod pomocí `WebMethod` atributu ve webových službách k označení toho, že by měla být metoda volat přes protokol SOAP. Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.  
  
- Popisuje způsob zařazení parametrů metody při spolupráci s nativním kódem. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  
  
- Popisuje vlastnosti modelu COM pro třídy, metody a rozhraní.  
  
- Volání nespravovaného kódu <xref:System.Runtime.InteropServices.DllImportAttribute> pomocí třídy.  
  
- Popisuje vaše sestavení s ohledem na název, verzi, popis nebo ochrannou známku.  
  
- Popisuje, kteří členové třídy mají být serializováni k trvalému serializaci.  
  
- Popisuje, jak mapovat mezi členy třídy a uzly XML pro serializaci kódu XML.  
  
- Popisuje požadavky na zabezpečení pro metody.  
  
- Určení vlastností používaných k vymáhání zabezpečení.  
  
- Řízení optimalizace pomocí kompilátoru JIT (just-in-time), takže kód zůstane snadno laděn.  
  
- Získání informací o volajícím metody.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
- [Vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
- [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
- [Postupy: Vytvoření C/C++ sjednocení pomocí atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
- [Společné atributy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
- [Informace o volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atributy](../../../../standard/attributes/index.md)
