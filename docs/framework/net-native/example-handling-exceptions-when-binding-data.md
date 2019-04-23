---
title: 'Příklad: Zpracování výjimek při vázání dat'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25b2117de40bbe7ba36fab028526116fc01ae09b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199892"
---
# <a name="example-handling-exceptions-when-binding-data"></a>Příklad: Zpracování výjimek při vázání dat
> [!NOTE]
>  Toto téma odkazuje na .NET Native Developer Preview, což je předběžná verze softwaru. Preview z si můžete stáhnout [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).  
  
 Následující příklad ukazuje, jak vyřešit [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimka, která je vyvolána při kompilaci aplikace s [!INCLUDE[net_native](../../../includes/net-native-md.md)] řetězce nástrojů se pokusí svázat data. Tady je informace o výjimce:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 Tady je přidružené volání zásobníku:  
  
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
 Základní zásobníku, snímků z <xref:Windows.UI.Xaml?displayProperty=nameWithType> obor názvů znamenat, že byl spuštěn modul vykreslování XAML.   Použití <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> metoda označuje založenými na reflexi vyhledávání hodnoty vlastnosti v typu, jehož metadata byla odebrána.  
  
 Prvním krokem při poskytování metadat směrnice by pro přidání `serialize` metadat pro typ tak, aby její vlastnosti jsou všechny dostupné:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>Je to izolované případu?  
 V tomto scénáři, kdy datové vazby má neúplný metadata pro jeden `ViewModel`, může pro ostatní uživatele, příliš.  Pokud kód je strukturována tak, aby aplikace zobrazit modely jsou všechny na `App.ViewModels` obor názvů, můžete použít další obecné direktivy modulu runtime:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>Může být kód přepsán nechcete použít reflexe?  
 Datová vazba je náročné na reflexi, změny kódu, aby se zabránilo reflexe není vhodná.  
  
 Existují však způsoby, jak určit `ViewModel` na stránku XAML tak, aby řetězce nástrojů můžete přidružit vlastnost vazby pomocí správného typu v době kompilace a zachovat metadata bez použití direktivy modulu runtime.  Například můžete použít <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> atribut na vlastnosti. To způsobí, že kompilátor XAML generovat informace o požadované vyhledávání a se vyhnete nutnosti direktivy modulu runtime v souboru Default.rd.xml.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [Příklad: Řešení potíží s dynamickým programováním](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
