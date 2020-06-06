---
title: 'Příklad: Zpracování výjimek při vázání dat'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
ms.openlocfilehash: b774d1bce4f4d1c03258ed44b27d3871e7c5275f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181025"
---
# <a name="example-handling-exceptions-when-binding-data"></a>Příklad: Zpracování výjimek při vázání dat
> [!NOTE]
> Toto téma se týká .NET Native Developer Preview, což je předběžná verze softwaru. Verzi Preview si můžete stáhnout z [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).  
  
 Následující příklad ukazuje, jak vyřešit výjimku [MissingMetadataException](missingmetadataexception-class-net-native.md) , která je vyvolána, když se aplikace zkompiluje s řetězem nástrojů .NET Native pokusí vytvořit vazby dat. Zde jsou informace o výjimce:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:
App.ViewModels.MainPageVM  
```  
  
 Tady je přidružený zásobník volání:  
  
```output
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a>Co aplikace právě dělala?  
 Na bázi zásobníku, snímky z <xref:Windows.UI.Xaml?displayProperty=nameWithType> oboru názvů označují, že modul vykreslování XAML byl spuštěn.   Použití <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> metody označuje vyhledávání na základě reflexe hodnoty vlastnosti u typu, jehož metadata byla odebrána.  
  
 Prvním krokem při poskytování direktivy metadata by bylo přidat `serialize` metadata pro typ tak, aby byly všechny vlastnosti dostupné:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>Jedná se o izolovaný případ?  
 V tomto scénáři, pokud datová vazba má neúplná metadata pro jednu `ViewModel` , může to být také pro ostatní.  Pokud je kód strukturovaný způsobem, že jsou všechny modely zobrazení aplikace v `App.ViewModels` oboru názvů, můžete použít obecnější direktivu modulu runtime:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>Je možné přepsat kód, aby nepoužíval reflexi?  
 Vzhledem k tomu, že vázání dat je náročné na reflexi, změna kódu tak, aby nedocházelo k neproveditelnému  
  
 Existují však způsoby, jak zadat na `ViewModel` stránku XAML, aby řetěz nástrojů mohl přidružit vazby vlastností ke správnému typu v době kompilace a zachovat metadata bez použití direktivy runtime.  Můžete například použít <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> atribut u vlastností. To způsobí, že kompilátor XAML vygeneruje požadované vyhledávací informace a vyhne se vyžadování direktivy modulu runtime ve výchozím souboru. Rd. XML.  
  
## <a name="see-also"></a>Viz také

- [Začínáme](getting-started-with-net-native.md)
- [Příklad: Řešení potíží s dynamickým programováním](example-troubleshooting-dynamic-programming.md)
