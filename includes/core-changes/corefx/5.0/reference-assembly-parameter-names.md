---
ms.openlocfilehash: abcab63b5a90a70cc9dfabb031e94ce379e5471b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720183"
---
### <a name="parameter-names-changed-in-reference-assemblies"></a><span data-ttu-id="b3a54-101">Názvy parametrů se změnily v referenčních sestaveních.</span><span class="sxs-lookup"><span data-stu-id="b3a54-101">Parameter names changed in reference assemblies</span></span>

<span data-ttu-id="b3a54-102">Některé názvy parametrů referenčního sestavení se změnily tak, aby odpovídaly názvům parametrů v sestaveních implementace.</span><span class="sxs-lookup"><span data-stu-id="b3a54-102">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b3a54-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="b3a54-103">Change description</span></span>

<span data-ttu-id="b3a54-104">V předchozích verzích rozhraní .NET se některé názvy parametrů [sestavení odkazů](../../../../docs/standard/assembly/reference-assemblies.md) liší podle jejich odpovídajících parametrů v sestavení implementace.</span><span class="sxs-lookup"><span data-stu-id="b3a54-104">In previous .NET versions, some [reference assembly](../../../../docs/standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="b3a54-105">To může způsobit problémy při použití pojmenovaných argumentů a reflexe.</span><span class="sxs-lookup"><span data-stu-id="b3a54-105">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="b3a54-106">V rozhraní .NET 5,0 byly tyto neshodné názvy parametrů aktualizovány v referenčních sestaveních tak, aby přesně odpovídaly názvům odpovídajících parametrů v sestaveních implementace.</span><span class="sxs-lookup"><span data-stu-id="b3a54-106">In .NET 5.0, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="b3a54-107">Následující tabulka uvádí názvy rozhraní API a parametrů, které se změnily.</span><span class="sxs-lookup"><span data-stu-id="b3a54-107">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="b3a54-108">rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b3a54-108">API</span></span> | <span data-ttu-id="b3a54-109">Starý název parametru</span><span class="sxs-lookup"><span data-stu-id="b3a54-109">Old parameter name</span></span> | <span data-ttu-id="b3a54-110">Nový název parametru</span><span class="sxs-lookup"><span data-stu-id="b3a54-110">New parameter name</span></span> |
| - | - | - |
| <xref:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)?displayProperty=nameWithType> | `stms` | `stmts` |
| <xref:System.Drawing.Icon.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | `si` |
| <xref:System.Drawing.Image.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | `si` |
| <xref:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})?displayProperty=nameWithType> | `ipString` | `ipSpan` |
| <xref:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)?displayProperty=nameWithType> | `ipString` | `ipSpan` |
| <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=nameWithType> | `buffer` | `array` |
| <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=nameWithType> | `buffer` | `array` |
| <xref:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)?displayProperty=nameWithType> | `authType` | `authenticationType` |
| <xref:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)?displayProperty=nameWithType> | `o` | `obj` |
| <xref:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)?displayProperty=nameWithType> | `value` | `obj` |
| <xref:System.Diagnostics.StackFrame.%23ctor(System.Boolean)> | `fNeedFileInfo` | `needFileInfo` |
| <xref:System.Diagnostics.StackFrame.%23ctor(System.Int32,System.Boolean)> | `fNeedFileInfo` | `needFileInfo` |
| <xref:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.IsNormalized(System.String)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.Normalize(System.String)?displayProperty=nameWithType> | `value` | `strInput` |

#### <a name="reason-for-change"></a><span data-ttu-id="b3a54-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="b3a54-111">Reason for change</span></span>

<span data-ttu-id="b3a54-112">Názvy parametrů se změnily na konzistenci a aby se předešlo chybám při použití pojmenovaných argumentů a reflexe.</span><span class="sxs-lookup"><span data-stu-id="b3a54-112">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b3a54-113">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b3a54-113">Version introduced</span></span>

<span data-ttu-id="b3a54-114">5,0</span><span class="sxs-lookup"><span data-stu-id="b3a54-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b3a54-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b3a54-115">Recommended action</span></span>

<span data-ttu-id="b3a54-116">Pokud dojde k chybě kompilátoru z důvodu změny názvu parametru, aktualizujte odpovídající název parametru.</span><span class="sxs-lookup"><span data-stu-id="b3a54-116">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

#### <a name="category"></a><span data-ttu-id="b3a54-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b3a54-117">Category</span></span>

<span data-ttu-id="b3a54-118">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="b3a54-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b3a54-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b3a54-119">Affected APIs</span></span>

- <xref:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)?displayProperty=fullName>
- <xref:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)?displayProperty=fullName>
- <xref:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)?displayProperty=fullName>
- <xref:System.Diagnostics.StackFrame.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackFrame.%23ctor(System.Int32,System.Boolean)>
- <xref:System.Drawing.Icon.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=fullName>
- <xref:System.Drawing.Image.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=fullName>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})?displayProperty=fullName>
- <xref:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)?displayProperty=fullName>
- <xref:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.IsNormalized(System.String)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.Normalize(System.String)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)`
- `M:System.Diagnostics.StackFrame.#ctor(System.Boolean)`
- `M:System.Diagnostics.StackFrame.#ctor(System.Int32,System.Boolean)`
- `M:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)`
- `M:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})`
- `M:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)`
- `M:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)`
- `M:System.StringNormalizationExtensions.IsNormalized(System.String)`
- `M:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)`
- `M:System.StringNormalizationExtensions.Normalize(System.String)`
- `M:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)`
- `M:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)`
- `M:System.Drawing.Icon.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Drawing.Image.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`

-->
