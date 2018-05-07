---
title: 'Příklad: Zpracování výjimek, pokud vazba dat'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c4b73ed36d3334e983b960ce972292a190bad85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="example-handling-exceptions-when-binding-data"></a>Příklad: Zpracování výjimek, pokud vazba dat
> [!NOTE]
>  Toto téma se týká .NET nativní Developer Preview, což je předběžná verze softwaru. Preview z si můžete stáhnout [webu Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).  
  
 Následující příklad ukazuje, jak vyřešit [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimka, která se vyvolá, když aplikace, kompilovat s [!INCLUDE[net_native](../../../includes/net-native-md.md)] řetězu nástroj pokusí vázat data. Tady je informace o výjimce:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 Tady je zásobníku přidružené volání:  
  
```  
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
  
## <a name="what-was-the-app-doing"></a>Co dělal aplikace?  
 Na bázi zásobníku, rámců z [Windows.UI.Xaml](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) obor názvů znamenat, že byla spuštěna modul vykreslování XAML.   Použití <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> metoda označuje vyhledávání na základě reflexe hodnoty vlastnosti na typ, jejichž metadata byla odebrána.  
  
 Prvním krokem při poskytování direktivu metadata by přidat `serialize` metadata pro typ tak, aby jeho vlastnosti jsou všechny dostupné:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>Je to izolované případ?  
 V tomto scénáři, pokud má datová vazba neúplné metadata pro jednu `ViewModel`, může se příliš ostatní uživatelé.  Pokud jsou strukturovaná kód tak, aby aplikace zobrazit modely jsou v `App.ViewModels` obor názvů, můžete použít obecnější direktivy modulu runtime:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>By mohla být přepsána kód nechcete použít reflexe?  
 Datová vazba je velmi náročná na výkon reflexe, a proto Změna kódu, aby se zabránilo reflexe není vhodná.  
  
 Existují však způsobů určení `ViewModel` na stránku XAML tak, aby nástroj řetězu můžete přidružit vlastnost vazby pomocí správného typu v doba kompilace a zachovat metadata bez použití direktivy modulu runtime.  Například je možné aplikovat [Windows.UI.Xaml.Data.BindableAttribute](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) atribut na vlastnosti. To způsobí, že kompilátor jazyka XAML generovat informace o požadované vyhledávání a zabraňuje nutnosti direktivy modulu runtime v souboru Default.rd.xml.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Příklad: Řešení potíží s dynamickým programováním](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
