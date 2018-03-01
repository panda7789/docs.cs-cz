---
title: "Postupy: Ruční vytváření obálek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5451599a5421149a7dc99ced6a42bb8220af247a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="def6f-102">Postupy: Ruční vytváření obálek</span><span class="sxs-lookup"><span data-stu-id="def6f-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="def6f-103">Rozhodnete-li se deklarovat typy modelu COM ve spravovaném zdrojovém kódu ručně, bude nejlépe, když začnete se stávajícím souborem IDL (Interface Definition Language) nebo knihovnou typů.</span><span class="sxs-lookup"><span data-stu-id="def6f-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="def6f-104">Nemáte-li k dispozici soubor IDL nebo nelze vygenerovat soubor knihovny typů, můžete typy modelu COM nasimulovat pomocí spravovaných deklarací a exportováním výsledného sestavení do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="def6f-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="def6f-105">Simulace typů modelu COM ze spravovaného prostředku</span><span class="sxs-lookup"><span data-stu-id="def6f-105">To simulate COM types from managed source</span></span>  
  
1.  <span data-ttu-id="def6f-106">Deklarujte typy v jazyce, který je kompatibilní se specifikací CLS (Common Language Specification), a soubor zkompilujte.</span><span class="sxs-lookup"><span data-stu-id="def6f-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2.  <span data-ttu-id="def6f-107">Export sestavení obsahující typů s [Exportér knihovny typů (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="def6f-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3.  <span data-ttu-id="def6f-108">Exportovanou knihovnu typů modelu COM použijte jako základ pro deklaraci spravovaných typů orientovaných na model COM.</span><span class="sxs-lookup"><span data-stu-id="def6f-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="def6f-109">Vytvoření obálky volatelné za běhu (RCW)</span><span class="sxs-lookup"><span data-stu-id="def6f-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1.  <span data-ttu-id="def6f-110">Za předpokladu, že máte soubor IDL nebo soubor knihovny typů, se rozhodněte, které třídy a rozhraní budou zahrnuty do uživatelského objektu RCW.</span><span class="sxs-lookup"><span data-stu-id="def6f-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="def6f-111">Je možné vyloučit jakékoli typy, které nechcete přímo nebo nepřímo použít v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="def6f-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2.  <span data-ttu-id="def6f-112">Vytvořte zdrojový soubor v jazyce, který odpovídá specifikaci CLS a deklarujte typy.</span><span class="sxs-lookup"><span data-stu-id="def6f-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="def6f-113">V tématu [knihovny typů pro souhrn konverze sestavení](http://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958) úplný popis procesu převodu importu.</span><span class="sxs-lookup"><span data-stu-id="def6f-113">See [Type Library to Assembly Conversion Summary](http://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958) for a complete description of the import conversion process.</span></span> <span data-ttu-id="def6f-114">Efektivní, když vytvoříte vlastní RCW, ručně provádíte typu Aktivita převod poskytované [Importér knihovny typů (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="def6f-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="def6f-115">Příklad v následující části zobrazuje typy v souboru IDL nebo souboru knihovny typů a odpovídající typy v kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="def6f-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3.  <span data-ttu-id="def6f-116">Po dokončení vytváření deklarací zkompilujte soubor jako jakýkoli jiný spravovaný zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="def6f-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4.  <span data-ttu-id="def6f-117">Stejně jako v případě typů, které jsou importovány pomocí nástroje Tlbimp.exe, vyžadují některé z nich dodatečné informace, které lze přidat přímo do kódu.</span><span class="sxs-lookup"><span data-stu-id="def6f-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="def6f-118">Podrobnosti najdete v tématu [postupy: sestavení zprostředkovatel komunikace s objekty upravit](http://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277).</span><span class="sxs-lookup"><span data-stu-id="def6f-118">For details, see [How to: Edit Interop Assemblies](http://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277).</span></span>  
  
## <a name="example"></a><span data-ttu-id="def6f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="def6f-119">Example</span></span>  
 <span data-ttu-id="def6f-120">Následující kód znázorňuje příklad rozhraní `ISATest` a třídy `SATest` v souboru IDL a odpovídající typy ve zdrojovém kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="def6f-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="def6f-121">**IDL nebo zadejte soubor knihovny**</span><span class="sxs-lookup"><span data-stu-id="def6f-121">**IDL or type library file**</span></span>  
  
```  
 [  
object,  
uuid(40A8C65D-2448-447A-B786-64682CBEF133),  
dual,  
helpstring("ISATest Interface"),  
pointer_default(unique)  
 ]  
interface ISATest : IDispatch  
 {  
[id(1), helpstring("method InSArray")]   
HRESULT InSArray([in] SAFEARRAY(int) *ppsa, [out,retval] int *pSum);  
 };  
 [  
uuid(116CCA1E-7E39-4515-9849-90790DA6431E),  
helpstring("SATest Class")  
 ]  
coclass SATest  
 {  
  [default] interface ISATest;  
 };  
```  
  
 <span data-ttu-id="def6f-122">**Obálka ve zdrojovém spravovaného kódu**</span><span class="sxs-lookup"><span data-stu-id="def6f-122">**Wrapper in managed source code**</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
using System.Runtime.CompilerServices;  
  
[assembly:Guid("E4A992B8-6F5C-442C-96E7-C4778924C753")]  
[assembly:ImportedFromTypeLib("SAServerLib")]  
namespace SAServer  
{  
 [ComImport]  
 [Guid("40A8C65D-2448-447A-B786-64682CBEF133")]  
 [TypeLibType(TypeLibTypeFlags.FLicensed)]  
 public interface ISATest  
 {  
  [DispId(1)]  
  //[MethodImpl(MethodImplOptions.InternalCall,  
  // MethodCodeType=MethodCodeType.Runtime)]  
  int InSArray( [MarshalAs(UnmanagedType.SafeArray,  
      SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }   
 [ComImport]  
 [Guid("116CCA1E-7E39-4515-9849-90790DA6431E")]  
 [ClassInterface(ClassInterfaceType.None)]  
 [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
 public class SATest : ISATest  
 {  
  [DispId(1)]  
  [MethodImpl(MethodImplOptions.InternalCall,   
  MethodCodeType=MethodCodeType.Runtime)]  
  extern int ISATest.InSArray( [MarshalAs(UnmanagedType.SafeArray,   
  SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="def6f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="def6f-123">See Also</span></span>  
 [<span data-ttu-id="def6f-124">Běhové obálky s možností přizpůsobení</span><span class="sxs-lookup"><span data-stu-id="def6f-124">Customizing Runtime Callable Wrappers</span></span>](http://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be)  
 [<span data-ttu-id="def6f-125">COM datové typy</span><span class="sxs-lookup"><span data-stu-id="def6f-125">COM Data Types</span></span>](http://msdn.microsoft.com/library/f93ae35d-a416-4218-8700-c8218cc90061)  
 [<span data-ttu-id="def6f-126">Postupy: Úprava spolupráce – sestavení</span><span class="sxs-lookup"><span data-stu-id="def6f-126">How to: Edit Interop Assemblies</span></span>](http://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277)  
 [<span data-ttu-id="def6f-127">Knihovny typů pro souhrn konverze sestavení</span><span class="sxs-lookup"><span data-stu-id="def6f-127">Type Library to Assembly Conversion Summary</span></span>](http://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 [<span data-ttu-id="def6f-128">Tlbimp.exe (importér knihovny typů)</span><span class="sxs-lookup"><span data-stu-id="def6f-128">Tlbimp.exe (Type Library Importer)</span></span>](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [<span data-ttu-id="def6f-129">Tlbexp.exe (exportér knihovny typů)</span><span class="sxs-lookup"><span data-stu-id="def6f-129">Tlbexp.exe (Type Library Exporter)</span></span>](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)
