---
title: Atributy (C#)
ms.date: 07/20/2015
ms.assetid: f148f13f-a0d5-4f22-9c87-4b73d5dde270
ms.openlocfilehash: a7e64c29ab8ca56a47ec6554ebc316f4922d3aca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="attributes-c"></a>Atributy (C#)
Atributy poskytují výkonný metoda spojování metadata nebo deklarativní informace s kódem (sestavení, typy, metody, vlastnosti a tak dále). Po atribut je spojen s entitou program, může být dotazován atribut v době běhu pomocí techniky názvem *reflexe*. Další informace najdete v tématu [reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md).  
  
 Atributy mít následující vlastnosti:  
  
-   Atributy přidat metadata do programu. *Metadata* je informace o typech definované v programu. Všechny sestavení .NET obsahovat zadanou sadu metadata, která popisuje typy a členy typu definované v sestavení. Můžete přidat vlastní atributy pro žádné další informace, které jsou potřeba. Další informace najdete v tématu, [vytváření vlastní atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
-   Celý sestavení, moduly nebo menší program prvky, jako jsou například třídy a vlastnosti, můžete použít jeden nebo více atributů.  
  
-   Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.  
  
-   Váš program můžete zkontrolovat svůj vlastní metadata nebo metadata v ostatních aplikacích pomocí reflexe. Další informace najdete v tématu [přístup k atributy podle pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="using-attributes"></a>Pomocí atributů  
 Atributy je možné použít u libovolného deklarace, když konkrétní atribut může omezit přístup k deklarace, na kterých je platný. V jazyce C# můžete určit atribut umístěním název atributu, uzavřeny do hranatých závorek ([]), nad deklaraci entity, které se.  
  
 V tomto příkladu <xref:System.SerializableAttribute> atribut se používá k aplikování zvláštní vlastností pro třídu:  
  
```csharp  
[System.Serializable]  
public class SampleClass  
{  
    // Objects of this type can be serialized.  
}  
```  
  
 Metody s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarován takto:  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
[System.Runtime.InteropServices.DllImport("user32.dll")]  
extern static void SampleMethod();  
```  
  
 Více než jeden atribut je možné použít u deklaraci:  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
void MethodA([In][Out] ref double x) { }  
void MethodB([Out][In] ref double x) { }  
void MethodC([In, Out] ref double x) { }  
```  
  
 Některé atributy lze zadat více než jednou pro danou entitu. Je například multiuse atribut <xref:System.Diagnostics.ConditionalAttribute>:  
  
```csharp  
[Conditional("DEBUG"), Conditional("TEST1")]  
void TraceMethod()  
{  
    // ...  
}  
```  
  
> [!NOTE]
>  Podle konvence ukončete všechny názvy atributů slovem "Atribut" jej odlišit od jiných položek v rozhraní .NET Framework. Však není potřeba zadejte příponu atribut při použití atributů v kódu. Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, ale `DllImportAttribute` je skutečný název atributu v rozhraní .NET Framework.  
  
### <a name="attribute-parameters"></a>Atribut parametry  
 Počet atributů mít parametry, které může být poziční, nepojmenovaný nebo s názvem. Žádné poziční parametry musí být zadaný v určitém pořadí a nelze jej vynechat; pojmenované parametry jsou volitelné a lze jej zadat v libovolném pořadí. Nejprve jsou zadány poziční parametry. Například odpovídají tyto tři atributy:  
  
```csharp  
[DllImport("user32.dll")]  
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]  
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]  
```  
  
 První parametr název DLL je poziční a dodává se vždy první; ostatní s názvem. V takovém případě i s názvem výchozí parametry na hodnotu false, můžete vynechat. Vyhledejte jednotlivé atributy dokumentaci informace o výchozí hodnoty parametrů.  
  
### <a name="attribute-targets"></a>Cíle atributů  
 *Cíl* atributu je ta entita, na které se vztahuje atribut. Atribut může například použít třídu, konkrétní metody nebo celé sestavení. Ve výchozím nastavení atribut vztahuje k elementu, který ho předchází. Ale můžete také explicitně identifikovat, například zda atribut se použije na metodu, nebo její parametr nebo hodnoty.  
  
 K identifikaci explicitně atribut target, použijte následující syntaxi:  
  
```csharp  
[target : attribute-list]  
```  
  
 Seznam možných `target` hodnoty je uvedené v následující tabulce.  
  
|Hodnota cíle|Platí pro|  
|------------------|----------------|  
|`assembly`|Celý sestavení|  
|`module`|Aktuální modul sestavení|  
|`field`|Pole ve třídě nebo struktury|  
|`event`|Událost|  
|`method`|Metoda nebo `get` a `set` vlastnost přístupové objekty|  
|`param`|Parametry metody nebo `set` parametry přistupující objekt vlastnosti|  
|`property`|Vlastnost|  
|`return`|Návratová hodnota metody, vlastnosti indexer nebo `get` přistupující objekt vlastnosti|  
|`type`|Struktura, třídu, rozhraní, výčet nebo delegáta|  
  
 Následující příklad ukazuje, jak chcete použít atributy pro sestavení a moduly. Další informace najdete v tématu [běžné atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).  
  
```csharp  
using System;  
using System.Reflection;  
[assembly: AssemblyTitleAttribute("Production assembly 4")]  
[module: CLSCompliant(true)]  
```  
  
 Následující příklad ukazuje, jak se má použít k metodám, metoda parametry, atributy a metoda návratové hodnoty v jazyce C#.  
  
```csharp  
// default: applies to method  
[SomeAttr]  
int Method1() { return 0; }  
  
// applies to method  
[method: SomeAttr]  
int Method2() { return 0; }  
  
// applies to return value  
[return: SomeAttr]  
int Method3() { return 0; }  
```  
  
> [!NOTE]
>  Bez ohledu na to cíle, na kterém `SomeAttr` je definován jako platný, `return` cíl musí být zadaný, i když `SomeAttr` byly definovány se provádí pouze návratové hodnoty. Jinými slovy, nebude používat kompilátor `AttributeUsage` informace týkající se řešení cíle nejednoznačný atributů. Další informace najdete v tématu [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).  
  
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
  
-   [Vytváření vlastních atributů (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [Přístup k atributům pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [Postupy: vytváření sjednocení C/C++ pomocí atributů (C#)](../../../../csharp/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [Mezi běžné atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [Informace o subjektu volajícím (C#)](../../../../csharp/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
 [Reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Atributy](../../../../../docs/standard/attributes/index.md)
