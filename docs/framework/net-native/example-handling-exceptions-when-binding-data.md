---
title: 'Příklad: Zpracování výjimek při vázání dat'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f7c40d1a179c29c3b92ca37848db6d1383e5d2d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049890"
---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="47df7-102">Příklad: Zpracování výjimek při vázání dat</span><span class="sxs-lookup"><span data-stu-id="47df7-102">Example: Handling Exceptions When Binding Data</span></span>
> [!NOTE]
> <span data-ttu-id="47df7-103">Toto téma se týká .NET Native Developer Preview, což je předběžná verze softwaru.</span><span class="sxs-lookup"><span data-stu-id="47df7-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="47df7-104">Verzi Preview si můžete stáhnout z [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).</span><span class="sxs-lookup"><span data-stu-id="47df7-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="47df7-105">Následující příklad ukazuje, jak vyřešit výjimku [MissingMetadataException](missingmetadataexception-class-net-native.md) , která je vyvolána, když se aplikace zkompiluje s řetězem nástrojů .NET Native pokusí vytvořit vazby dat.</span><span class="sxs-lookup"><span data-stu-id="47df7-105">The following example shows how to resolve a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the .NET Native tool chain tries to bind data.</span></span> <span data-ttu-id="47df7-106">Zde jsou informace o výjimce:</span><span class="sxs-lookup"><span data-stu-id="47df7-106">Here’s the exception information:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="47df7-107">Tady je přidružený zásobník volání:</span><span class="sxs-lookup"><span data-stu-id="47df7-107">Here's the associated call stack:</span></span>  
  
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
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="47df7-108">Jakou aplikaci dělá?</span><span class="sxs-lookup"><span data-stu-id="47df7-108">What was the app doing?</span></span>  
 <span data-ttu-id="47df7-109">Na bázi zásobníku, snímky z <xref:Windows.UI.Xaml?displayProperty=nameWithType> oboru názvů označují, že modul vykreslování XAML byl spuštěn.</span><span class="sxs-lookup"><span data-stu-id="47df7-109">At the base of the stack, frames from the <xref:Windows.UI.Xaml?displayProperty=nameWithType> namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="47df7-110">Použití <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> metody označuje vyhledávání na základě reflexe hodnoty vlastnosti u typu, jehož metadata byla odebrána.</span><span class="sxs-lookup"><span data-stu-id="47df7-110">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="47df7-111">Prvním krokem při poskytování direktivy metadata by bylo přidat `serialize` metadata pro typ tak, aby byly všechny vlastnosti dostupné:</span><span class="sxs-lookup"><span data-stu-id="47df7-111">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="47df7-112">Jedná se o izolovaný případ?</span><span class="sxs-lookup"><span data-stu-id="47df7-112">Is this an isolated case?</span></span>  
 <span data-ttu-id="47df7-113">V tomto scénáři, pokud datová vazba má neúplná metadata pro `ViewModel`jednu, může to být také pro ostatní.</span><span class="sxs-lookup"><span data-stu-id="47df7-113">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="47df7-114">Pokud je kód strukturovaný způsobem, že jsou všechny modely zobrazení aplikace v `App.ViewModels` oboru názvů, můžete použít obecnější direktivu modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="47df7-114">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="47df7-115">Je možné přepsat kód, aby nepoužíval reflexi?</span><span class="sxs-lookup"><span data-stu-id="47df7-115">Could the code be rewritten to not use reflection?</span></span>  
 <span data-ttu-id="47df7-116">Vzhledem k tomu, že vázání dat je náročné na reflexi, změna kódu tak, aby nedocházelo k neproveditelnému</span><span class="sxs-lookup"><span data-stu-id="47df7-116">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="47df7-117">Existují však způsoby, jak zadat `ViewModel` na stránku XAML, aby řetěz nástrojů mohl přidružit vazby vlastností ke správnému typu v době kompilace a zachovat metadata bez použití direktivy runtime.</span><span class="sxs-lookup"><span data-stu-id="47df7-117">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="47df7-118">Můžete například použít <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> atribut u vlastností.</span><span class="sxs-lookup"><span data-stu-id="47df7-118">For example, you could apply the <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> attribute on properties.</span></span> <span data-ttu-id="47df7-119">To způsobí, že kompilátor XAML vygeneruje požadované vyhledávací informace a vyhne se vyžadování direktivy modulu runtime ve výchozím souboru. Rd. XML.</span><span class="sxs-lookup"><span data-stu-id="47df7-119">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47df7-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47df7-120">See also</span></span>

- [<span data-ttu-id="47df7-121">Začínáme</span><span class="sxs-lookup"><span data-stu-id="47df7-121">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="47df7-122">Příklad: Řešení potíží s dynamickým programováním</span><span class="sxs-lookup"><span data-stu-id="47df7-122">Example: Troubleshooting Dynamic Programming</span></span>](example-troubleshooting-dynamic-programming.md)
