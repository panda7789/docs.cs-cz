---
title: ControlBuilderInterceptor – Třída
ms.date: 08/11/2020
api_name:
- System.Web.Compilation.ControlBuilderInterceptor
api_location:
- System.Web.dll
api_type:
- Assembly
topic_type:
- apiref
ms.openlocfilehash: 312d977f832d262b1bebc6638280b67b133babdf
ms.sourcegitcommit: 70d6a7e4f7187cbfa332f0f8be76566f7828cfcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88084393"
---
# <a name="controlbuilderinterceptor-class"></a><span data-ttu-id="8a9ac-102">ControlBuilderInterceptor – Třída</span><span class="sxs-lookup"><span data-stu-id="8a9ac-102">ControlBuilderInterceptor class</span></span>

<span data-ttu-id="8a9ac-103">`ControlBuilderInterceptor`Třída umožňuje proces kompilace přizpůsobit nebo řídit.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-103">The `ControlBuilderInterceptor` class allows the compilation process to be customized or controlled.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a9ac-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8a9ac-104">Syntax</span></span>

```csharp
internal class ControlBuilderInterceptor
```

> [!WARNING]
> <span data-ttu-id="8a9ac-105">`ControlBuilderInterceptor`Třída je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-105">The `ControlBuilderInterceptor` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="8a9ac-106">Jak je popsáno v části poznámky, existence tohoto typu lze zkontrolovat a zjistit, zda je k dispozici podpora typu zachytávací.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-106">As described in the Remarks section, the existence of this type can be checked to determine whether interceptor type support is present.</span></span> <span data-ttu-id="8a9ac-107">Společnost Microsoft v žádné situaci nepodporuje žádné jiné použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-107">Microsoft does not support any other use of this class in a production application under any circumstance.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a9ac-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a9ac-108">Remarks</span></span>

<span data-ttu-id="8a9ac-109">V .NET Framework 2,0 a .NET Framework 3,5 aktualizace [ze srpna 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) přidala podporu pro použití typu zachytávací pro přizpůsobení nebo řízení procesu kompilace.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-109">In .NET Framework 2.0 and .NET Framework 3.5, the [August 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) updates added support for using an interceptor type to customize or control the compilation process.</span></span> <span data-ttu-id="8a9ac-110">Můžete určit, zda je tato podpora přítomna, pomocí nástroje <xref:System.Type.GetType?displayProperty=nameWithType> pro kontrolu existence `ControlBuilderInterceptor` typu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-110">You can determine whether this support is present by using <xref:System.Type.GetType?displayProperty=nameWithType> to check the existence of the `ControlBuilderInterceptor` type, as demonstrated in the following code.</span></span>

```csharp
Type type = Type.GetType("System.Web.Compilation.ControlBuilderInterceptor, System.Web, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a");
```

<span data-ttu-id="8a9ac-111">Pokud vrácená hodnota je jiná než null, je k dispozici podpora pro zachycování.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-111">If the return value is non-null, then interceptor support is present.</span></span> <span data-ttu-id="8a9ac-112">Pokud je vrácená hodnota `null` , nebo pokud je vyvolána výjimka, pak aktualizace ze srpna 2020 nebyly nainstalovány a chybí podpora pro zachycování.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-112">If the return value is `null`, or if an exception is thrown, then the August 2020 updates have not been installed, and interceptor support is absent.</span></span>

<span data-ttu-id="8a9ac-113">Pokud je k dispozici podpora pro zachycování, můžete napsat a zaregistrovat typ zachytávací, který bude komunikovat s procesem kompilace stejným způsobem jako <xref:System.Web.Compilation.ControlBuilderInterceptor> v novějších verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-113">If interceptor support is present, you can write and register an interceptor type that will interact with the compilation process in exactly the same way that <xref:System.Web.Compilation.ControlBuilderInterceptor> does on later versions of .NET Framework.</span></span> <span data-ttu-id="8a9ac-114">V .NET Framework 2,0 a .NET Framework 3,5 může být typ zachytávací libovolná třída, která splňuje následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="8a9ac-114">In .NET Framework 2.0 and .NET Framework 3.5, the interceptor type can be any class that meets the following requirements:</span></span>

* <span data-ttu-id="8a9ac-115">Má veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-115">Has a public, parameterless constructor.</span></span>
* <span data-ttu-id="8a9ac-116">Má veřejné, nestatické metody s názvem `PreControlBuilderInit` a `OnProcessGeneratedCode` , které mají stejnou signaturu a sémantiku jako <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> metody a, které existují v novějších verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-116">Has public, non-static methods named `PreControlBuilderInit` and `OnProcessGeneratedCode` that have the same signature and semantics as the <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> and <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> methods, which exist in later versions of .NET Framework.</span></span>

<span data-ttu-id="8a9ac-117">Zaregistrujte typ zachytávací pomocí `aspnet:20ControlBuilderInterceptor` klíče v nastavení aplikace ASP.NET ( `<appSettings>` ).</span><span class="sxs-lookup"><span data-stu-id="8a9ac-117">Register the interceptor type by using the `aspnet:20ControlBuilderInterceptor` key in ASP.NET application settings (`<appSettings>`).</span></span> <span data-ttu-id="8a9ac-118">Toto nastavení aplikace musí být uvedené v počítači nebo v souboru aplikace *web.config* .</span><span class="sxs-lookup"><span data-stu-id="8a9ac-118">This application setting must be listed in your computer or application *web.config* file.</span></span> <span data-ttu-id="8a9ac-119">Zadejte typ zachytávací pomocí kvalifikovaného názvu typu sestavení.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-119">Specify the interceptor type by using its assembly-qualified type name.</span></span> <span data-ttu-id="8a9ac-120">Následující příklad ukazuje, jak zaregistrovat typ zachytávací s názvem `Fabrikam.Interceptor` .</span><span class="sxs-lookup"><span data-stu-id="8a9ac-120">The following example shows how to register an interceptor type named `Fabrikam.Interceptor`.</span></span>

```xml
<configuration>
  ...
  <appSettings>
    ...
    <add key="aspnet:20ControlBuilderInterceptor"
         value="Fabrikam.Interceptor, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
  </appSettings>
</configuration>

To retrieve the assembly-qualified name of a type, use the <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> property, as demonstrated in the following code.

```csharp
string assemblyQualifiedName = typeof(Fabrikam.Interceptor).AssemblyQualifiedName;
```

<span data-ttu-id="8a9ac-121">Pokud je k dispozici podpora pro zachycování, proces kompilace spolupracuje s uvedeným typem způsobem popsaným výše.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-121">When interceptor support is present, the compilation process interacts with the listed type in the manner described above.</span></span> <span data-ttu-id="8a9ac-122">Pokud chybí podpora pro zachycování, nastavení aplikace se ignoruje a nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="8a9ac-122">When interceptor support is absent, the application setting is ignored and has no effect.</span></span>

## <a name="requirements"></a><span data-ttu-id="8a9ac-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a9ac-123">Requirements</span></span>

<span data-ttu-id="8a9ac-124">**Obor názvů:** System. Web. Compilation</span><span class="sxs-lookup"><span data-stu-id="8a9ac-124">**Namespace:** System.Web.Compilation</span></span>

<span data-ttu-id="8a9ac-125">**Sestavení:** System. Web (v System.Web.dll)</span><span class="sxs-lookup"><span data-stu-id="8a9ac-125">**Assembly:** System.Web (in System.Web.dll)</span></span>

<span data-ttu-id="8a9ac-126">**Verze .NET Framework:** 3,5, 2,0</span><span class="sxs-lookup"><span data-stu-id="8a9ac-126">**.NET Framework versions:** 3.5, 2.0</span></span>
