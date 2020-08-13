---
title: ControlBuilderInterceptor – třída
ms.date: 08/11/2020
api_name:
- System.Web.Compilation.ControlBuilderInterceptor
api_location:
- System.Web.dll
api_type:
- Assembly
topic_type:
- apiref
ms.openlocfilehash: 0cd7409deb9cb84783cfa70600999fa4b2a2d2e2
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2020
ms.locfileid: "88187982"
---
# <a name="controlbuilderinterceptor-class"></a><span data-ttu-id="f069b-102">ControlBuilderInterceptor – třída</span><span class="sxs-lookup"><span data-stu-id="f069b-102">ControlBuilderInterceptor class</span></span>

<span data-ttu-id="f069b-103">`ControlBuilderInterceptor`Třída umožňuje proces kompilace přizpůsobit nebo řídit.</span><span class="sxs-lookup"><span data-stu-id="f069b-103">The `ControlBuilderInterceptor` class allows the compilation process to be customized or controlled.</span></span>

## <a name="syntax"></a><span data-ttu-id="f069b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f069b-104">Syntax</span></span>

```csharp
internal class ControlBuilderInterceptor
```

> [!WARNING]
> <span data-ttu-id="f069b-105">`ControlBuilderInterceptor`Třída je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="f069b-105">The `ControlBuilderInterceptor` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f069b-106">Jak je popsáno v části poznámky, existence tohoto typu lze zkontrolovat a zjistit, zda je k dispozici podpora typu zachytávací.</span><span class="sxs-lookup"><span data-stu-id="f069b-106">As described in the Remarks section, the existence of this type can be checked to determine whether interceptor type support is present.</span></span> <span data-ttu-id="f069b-107">Společnost Microsoft v žádné situaci nepodporuje žádné jiné použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f069b-107">Microsoft does not support any other use of this class in a production application under any circumstance.</span></span>

## <a name="remarks"></a><span data-ttu-id="f069b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f069b-108">Remarks</span></span>

<span data-ttu-id="f069b-109">V .NET Framework 2,0 a .NET Framework 3,5 aktualizace [ze srpna 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) přidala podporu pro použití typu zachytávací pro přizpůsobení nebo řízení procesu kompilace.</span><span class="sxs-lookup"><span data-stu-id="f069b-109">In .NET Framework 2.0 and .NET Framework 3.5, the [August 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) updates added support for using an interceptor type to customize or control the compilation process.</span></span> <span data-ttu-id="f069b-110">Můžete určit, zda je tato podpora přítomna, pomocí nástroje <xref:System.Type.GetType?displayProperty=nameWithType> pro kontrolu existence `ControlBuilderInterceptor` typu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f069b-110">You can determine whether this support is present by using <xref:System.Type.GetType?displayProperty=nameWithType> to check the existence of the `ControlBuilderInterceptor` type, as demonstrated in the following code.</span></span>

```csharp
Type type = Type.GetType("System.Web.Compilation.ControlBuilderInterceptor, System.Web, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a");
```

<span data-ttu-id="f069b-111">Pokud vrácená hodnota je jiná než null, je k dispozici podpora pro zachycování.</span><span class="sxs-lookup"><span data-stu-id="f069b-111">If the return value is non-null, then interceptor support is present.</span></span> <span data-ttu-id="f069b-112">Pokud je vrácená hodnota `null` , nebo pokud je vyvolána výjimka, pak aktualizace ze srpna 2020 nebyly nainstalovány a chybí podpora pro zachycování.</span><span class="sxs-lookup"><span data-stu-id="f069b-112">If the return value is `null`, or if an exception is thrown, then the August 2020 updates have not been installed, and interceptor support is absent.</span></span>

<span data-ttu-id="f069b-113">Pokud je k dispozici podpora pro zachycování, můžete napsat a zaregistrovat typ zachytávací, který bude komunikovat s procesem kompilace stejným způsobem jako <xref:System.Web.Compilation.ControlBuilderInterceptor> v novějších verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f069b-113">If interceptor support is present, you can write and register an interceptor type that will interact with the compilation process in exactly the same way that <xref:System.Web.Compilation.ControlBuilderInterceptor> does on later versions of .NET Framework.</span></span> <span data-ttu-id="f069b-114">V .NET Framework 2,0 a .NET Framework 3,5 může být typ zachytávací libovolná třída, která splňuje následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="f069b-114">In .NET Framework 2.0 and .NET Framework 3.5, the interceptor type can be any class that meets the following requirements:</span></span>

* <span data-ttu-id="f069b-115">Má veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="f069b-115">Has a public, parameterless constructor.</span></span>
* <span data-ttu-id="f069b-116">Má veřejné, nestatické metody s názvem `PreControlBuilderInit` a `OnProcessGeneratedCode` , které mají stejnou signaturu a sémantiku jako <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> metody a, které existují v novějších verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f069b-116">Has public, non-static methods named `PreControlBuilderInit` and `OnProcessGeneratedCode` that have the same signature and semantics as the <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> and <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> methods, which exist in later versions of .NET Framework.</span></span>

<span data-ttu-id="f069b-117">Zaregistrujte typ zachytávací pomocí `aspnet:20ControlBuilderInterceptor` klíče v nastavení aplikace ASP.NET ( `<appSettings>` ).</span><span class="sxs-lookup"><span data-stu-id="f069b-117">Register the interceptor type by using the `aspnet:20ControlBuilderInterceptor` key in ASP.NET application settings (`<appSettings>`).</span></span> <span data-ttu-id="f069b-118">Toto nastavení aplikace musí být uvedené v počítači nebo v souboru aplikace *web.config* .</span><span class="sxs-lookup"><span data-stu-id="f069b-118">This application setting must be listed in your computer or application *web.config* file.</span></span> <span data-ttu-id="f069b-119">Zadejte typ zachytávací pomocí kvalifikovaného názvu typu sestavení.</span><span class="sxs-lookup"><span data-stu-id="f069b-119">Specify the interceptor type by using its assembly-qualified type name.</span></span> <span data-ttu-id="f069b-120">Následující příklad ukazuje, jak zaregistrovat typ zachytávací s názvem `Fabrikam.Interceptor` .</span><span class="sxs-lookup"><span data-stu-id="f069b-120">The following example shows how to register an interceptor type named `Fabrikam.Interceptor`.</span></span>

```xml
<configuration>
  ...
  <appSettings>
    ...
    <add key="aspnet:20ControlBuilderInterceptor"
         value="Fabrikam.Interceptor, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
  </appSettings>
</configuration>
```

<span data-ttu-id="f069b-121">Chcete-li načíst název kvalifikovaný pro sestavení typu, použijte <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> vlastnost, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f069b-121">To retrieve the assembly-qualified name of a type, use the <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> property, as demonstrated in the following code.</span></span>

```csharp
string assemblyQualifiedName = typeof(Fabrikam.Interceptor).AssemblyQualifiedName;
```

<span data-ttu-id="f069b-122">Pokud je k dispozici podpora pro zachycování, proces kompilace spolupracuje s uvedeným typem způsobem popsaným výše.</span><span class="sxs-lookup"><span data-stu-id="f069b-122">When interceptor support is present, the compilation process interacts with the listed type in the manner described above.</span></span> <span data-ttu-id="f069b-123">Pokud chybí podpora pro zachycování, nastavení aplikace se ignoruje a nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="f069b-123">When interceptor support is absent, the application setting is ignored and has no effect.</span></span>

## <a name="requirements"></a><span data-ttu-id="f069b-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f069b-124">Requirements</span></span>

<span data-ttu-id="f069b-125">**Obor názvů:** System. Web. Compilation</span><span class="sxs-lookup"><span data-stu-id="f069b-125">**Namespace:** System.Web.Compilation</span></span>

<span data-ttu-id="f069b-126">**Sestavení:** System. Web (v System.Web.dll)</span><span class="sxs-lookup"><span data-stu-id="f069b-126">**Assembly:** System.Web (in System.Web.dll)</span></span>

<span data-ttu-id="f069b-127">**Verze .NET Framework:** 3,5, 2,0</span><span class="sxs-lookup"><span data-stu-id="f069b-127">**.NET Framework versions:** 3.5, 2.0</span></span>
