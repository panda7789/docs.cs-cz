---
title: 'Příklad: Zpracování výjimek při vázání dat'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
ms.openlocfilehash: b774d1bce4f4d1c03258ed44b27d3871e7c5275f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181025"
---
# <a name="example-handling-exceptions-when-binding-data"></a>Příklad: Zpracování výjimek při vázání dat
> [!NOTE]
> Toto téma odkazuje na nativní verzi preview pro vývojáře .NET, což je předběžný software. Náhled si můžete stáhnout z [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).  
  
 Následující příklad ukazuje, jak vyřešit [výjimku MissingMetadataException,](missingmetadataexception-class-net-native.md) která je vyvolána, když se aplikace zkompilovaná s řetězcem nástrojů .NET Native pokusí svázat data. Zde jsou informace o výjimce:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:
App.ViewModels.MainPageVM  
```  
  
 Tady je přidružený zásobník hovorů:  
  
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
 Na základně zásobníku rámce z <xref:Windows.UI.Xaml?displayProperty=nameWithType> oboru názvů označují, že byl spuštěn vykreslovací modul XAML.   Použití <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> metody označuje vyhledávání na základě reflexe hodnoty vlastnosti na typu, jehož metadata byla odebrána.  
  
 Prvním krokem při poskytování směrnice metadat by `serialize` bylo přidat metadata pro typ tak, aby jeho vlastnosti jsou přístupné:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>Je to ojedinělý případ?  
 V tomto scénáři pokud vazby dat `ViewModel`má neúplná metadata pro jeden , může pro ostatní, příliš.  Pokud je kód strukturován tak, aby všechny modely zobrazení `App.ViewModels` aplikace byly v oboru názvů, můžete použít obecnější direktivu runtime:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>Mohl by být kód přepsán tak, aby nepoužíval reflexi?  
 Vzhledem k tomu, že vazby dat je reflexe náročné, změna kódu, aby se zabránilo reflexe není možné.  
  
 Existují však způsoby, `ViewModel` jak určit stránku XAML tak, aby řetězec nástrojů může přidružit vazby vlastností ke správnému typu v době kompilace a zachovat metadata bez použití direktivy runtime.  Můžete například použít <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> atribut na vlastnosti. To způsobí, že kompilátor XAML vygeneruje požadované vyhledávací informace a vyhne se nutnosti direktivy runtime v souboru Default.rd.xml.  
  
## <a name="see-also"></a>Viz také

- [Začínáme](getting-started-with-net-native.md)
- [Příklad: Řešení potíží s dynamickým programováním](example-troubleshooting-dynamic-programming.md)
