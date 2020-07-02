---
title: 'Postupy: Ruční vytváření obálek'
description: Vytvořte obálky typů COM ručně. Použijte existující soubor IDL nebo knihovnu typů nebo vytvořte spravované deklarace a exportujte sestavení do knihovny typů.
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
ms.openlocfilehash: e562a7e963ff744bf9193821d54dd898db521464
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619582"
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="fb899-104">Postupy: Ruční vytváření obálek</span><span class="sxs-lookup"><span data-stu-id="fb899-104">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="fb899-105">Rozhodnete-li se deklarovat typy modelu COM ve spravovaném zdrojovém kódu ručně, bude nejlépe, když začnete se stávajícím souborem IDL (Interface Definition Language) nebo knihovnou typů.</span><span class="sxs-lookup"><span data-stu-id="fb899-105">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="fb899-106">Nemáte-li k dispozici soubor IDL nebo nelze vygenerovat soubor knihovny typů, můžete typy modelu COM nasimulovat pomocí spravovaných deklarací a exportováním výsledného sestavení do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fb899-106">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="fb899-107">Simulace typů modelu COM ze spravovaného prostředku</span><span class="sxs-lookup"><span data-stu-id="fb899-107">To simulate COM types from managed source</span></span>  
  
1. <span data-ttu-id="fb899-108">Deklarujte typy v jazyce, který je kompatibilní se specifikací CLS (Common Language Specification), a soubor zkompilujte.</span><span class="sxs-lookup"><span data-stu-id="fb899-108">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2. <span data-ttu-id="fb899-109">Exportujte sestavení obsahující typy pomocí [exportéra knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="fb899-109">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3. <span data-ttu-id="fb899-110">Exportovanou knihovnu typů modelu COM použijte jako základ pro deklaraci spravovaných typů orientovaných na model COM.</span><span class="sxs-lookup"><span data-stu-id="fb899-110">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="fb899-111">Vytvoření obálky volatelné za běhu (RCW)</span><span class="sxs-lookup"><span data-stu-id="fb899-111">To create a runtime callable wrapper (RCW)</span></span>  
  
1. <span data-ttu-id="fb899-112">Za předpokladu, že máte soubor IDL nebo soubor knihovny typů, se rozhodněte, které třídy a rozhraní budou zahrnuty do uživatelského objektu RCW.</span><span class="sxs-lookup"><span data-stu-id="fb899-112">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="fb899-113">Je možné vyloučit jakékoli typy, které nechcete přímo nebo nepřímo použít v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fb899-113">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2. <span data-ttu-id="fb899-114">Vytvořte zdrojový soubor v jazyce, který odpovídá specifikaci CLS a deklarujte typy.</span><span class="sxs-lookup"><span data-stu-id="fb899-114">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="fb899-115">Úplný popis procesu převodu importu naleznete v tématu [Souhrn převodu knihovny typů na sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="fb899-115">See [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) for a complete description of the import conversion process.</span></span> <span data-ttu-id="fb899-116">Efektivně, když vytváříte vlastní RCW, ručně provádíte aktivitu konverze typu poskytnutou modulem pro [Import knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="fb899-116">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="fb899-117">Příklad v následující části zobrazuje typy v souboru IDL nebo souboru knihovny typů a odpovídající typy v kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="fb899-117">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3. <span data-ttu-id="fb899-118">Po dokončení vytváření deklarací zkompilujte soubor jako jakýkoli jiný spravovaný zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="fb899-118">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4. <span data-ttu-id="fb899-119">Stejně jako v případě typů, které jsou importovány pomocí nástroje Tlbimp.exe, vyžadují některé z nich dodatečné informace, které lze přidat přímo do kódu.</span><span class="sxs-lookup"><span data-stu-id="fb899-119">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="fb899-120">Podrobnosti naleznete v tématu [How to: Edit interop assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fb899-120">For details, see [How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb899-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb899-121">Example</span></span>  
 <span data-ttu-id="fb899-122">Následující kód znázorňuje příklad rozhraní `ISATest` a třídy `SATest` v souboru IDL a odpovídající typy ve zdrojovém kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="fb899-122">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="fb899-123">**IDL nebo soubor knihovny typů**</span><span class="sxs-lookup"><span data-stu-id="fb899-123">**IDL or type library file**</span></span>  
  
```cpp
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
  
 <span data-ttu-id="fb899-124">**Obálka ve spravovaném zdrojovém kódu**</span><span class="sxs-lookup"><span data-stu-id="fb899-124">**Wrapper in managed source code**</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb899-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb899-125">See also</span></span>

- <span data-ttu-id="fb899-126">[Přizpůsobení obálek za běhu, které se budou volat](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fb899-126">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>
- <span data-ttu-id="fb899-127">[Datové typy COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fb899-127">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>
- <span data-ttu-id="fb899-128">[Postupy: Úprava sestavení vzájemné spolupráce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fb899-128">[How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span></span>
- <span data-ttu-id="fb899-129">[Souhrn převodu knihovny typů na sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fb899-129">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>
- [<span data-ttu-id="fb899-130">Tlbimp.exe (importér knihovny typů)</span><span class="sxs-lookup"><span data-stu-id="fb899-130">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="fb899-131">Tlbexp.exe (typ Exportér knihovny)</span><span class="sxs-lookup"><span data-stu-id="fb899-131">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
