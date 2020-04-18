---
ms.openlocfilehash: c858a2a614cce587afb456a963dfcf11cabf770c
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637168"
---
### <a name="obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed"></a><span data-ttu-id="608e2-101">Byla odebrána zastaralá antiforgerií, CORS, diagnostika, MVC a směrovací api</span><span class="sxs-lookup"><span data-stu-id="608e2-101">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>

<span data-ttu-id="608e2-102">Zastaralé členy a přepínače kompatibility v ASP.NET Core 2.2 byly odebrány.</span><span class="sxs-lookup"><span data-stu-id="608e2-102">Obsolete members and compatibility switches in ASP.NET Core 2.2 were removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="608e2-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="608e2-103">Version introduced</span></span>

<span data-ttu-id="608e2-104">3.0</span><span class="sxs-lookup"><span data-stu-id="608e2-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="608e2-105">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="608e2-105">Reason for change</span></span>

<span data-ttu-id="608e2-106">Zlepšení povrchu ROZHRANÍ API v průběhu času.</span><span class="sxs-lookup"><span data-stu-id="608e2-106">Improvement of API surface over time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="608e2-107">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="608e2-107">Recommended action</span></span>

<span data-ttu-id="608e2-108">Při cílení na rozhraní .NET Core 2.2 postupujte podle pokynů v zastaralých zprávách sestavení a přijměte místo toho nová rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="608e2-108">While targeting .NET Core 2.2, follow the guidance in the obsolete build messages to adopt new APIs instead.</span></span>

#### <a name="category"></a><span data-ttu-id="608e2-109">Kategorie</span><span class="sxs-lookup"><span data-stu-id="608e2-109">Category</span></span>

<span data-ttu-id="608e2-110">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="608e2-110">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="608e2-111">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="608e2-111">Affected APIs</span></span>

<span data-ttu-id="608e2-112">Následující typy a členy byly označeny jako zastaralé pro ASP.NET jádrem 2.1 a 2.2:</span><span class="sxs-lookup"><span data-stu-id="608e2-112">The following types and members were marked as obsolete for ASP.NET Core 2.1 and 2.2:</span></span>

<span data-ttu-id="608e2-113">**Typy**</span><span class="sxs-lookup"><span data-stu-id="608e2-113">**Types**</span></span>

- <span data-ttu-id="608e2-114">Microsoft.AspNetCore.Diagnostics.Views.WelcomePage</span><span class="sxs-lookup"><span data-stu-id="608e2-114">Microsoft.AspNetCore.Diagnostics.Views.WelcomePage</span></span>
- <span data-ttu-id="608e2-115">Microsoft.AspNetCore.DiagnosticsViewPage.Views.AttributeValue</span><span class="sxs-lookup"><span data-stu-id="608e2-115">Microsoft.AspNetCore.DiagnosticsViewPage.Views.AttributeValue</span></span>
- <span data-ttu-id="608e2-116">Microsoft.AspNetCore.DiagnosticsViewPage.Views.BaseView</span><span class="sxs-lookup"><span data-stu-id="608e2-116">Microsoft.AspNetCore.DiagnosticsViewPage.Views.BaseView</span></span>
- <span data-ttu-id="608e2-117">Microsoft.AspNetCore.DiagnosticsViewPage.Views.HelperVýsledek</span><span class="sxs-lookup"><span data-stu-id="608e2-117">Microsoft.AspNetCore.DiagnosticsViewPage.Views.HelperResult</span></span>
- <span data-ttu-id="608e2-118">Microsoft.AspNetCore.Mvc.Formatters.Xml.ProblemDetails21Obálka</span><span class="sxs-lookup"><span data-stu-id="608e2-118">Microsoft.AspNetCore.Mvc.Formatters.Xml.ProblemDetails21Wrapper</span></span>
- <span data-ttu-id="608e2-119">Microsoft.AspNetCore.Mvc.Formatters.Xml.ValidationProblemDetails21Obálka</span><span class="sxs-lookup"><span data-stu-id="608e2-119">Microsoft.AspNetCore.Mvc.Formatters.Xml.ValidationProblemDetails21Wrapper</span></span>
- <span data-ttu-id="608e2-120">Microsoft.AspNetCore.Mvc.Razor.Compilation.ViewsProvider</span><span class="sxs-lookup"><span data-stu-id="608e2-120">Microsoft.AspNetCore.Mvc.Razor.Compilation.ViewsFeatureProvider</span></span>
- <span data-ttu-id="608e2-121">Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.PageArgumentBinder</span><span class="sxs-lookup"><span data-stu-id="608e2-121">Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.PageArgumentBinder</span></span>
- <span data-ttu-id="608e2-122">Microsoft.AspNetCore.Routing.IRouteValuesAddressMetadata</span><span class="sxs-lookup"><span data-stu-id="608e2-122">Microsoft.AspNetCore.Routing.IRouteValuesAddressMetadata</span></span>
- <span data-ttu-id="608e2-123">Microsoft.AspNetCore.Routing.RouteValuesAddressMetadata</span><span class="sxs-lookup"><span data-stu-id="608e2-123">Microsoft.AspNetCore.Routing.RouteValuesAddressMetadata</span></span>

<span data-ttu-id="608e2-124">**Konstruktory**</span><span class="sxs-lookup"><span data-stu-id="608e2-124">**Constructors**</span></span>

- <span data-ttu-id="608e2-125">Microsoft.AspNetCore.Cors.Infrastructure.CorsService(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Cors.Infrastructure.CorsOptions})</span><span class="sxs-lookup"><span data-stu-id="608e2-125">Microsoft.AspNetCore.Cors.Infrastructure.CorsService(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Cors.Infrastructure.CorsOptions})</span></span>
- <span data-ttu-id="608e2-126">Microsoft.AspNetCore.Routing.Tree.TreeRouteBuilder(Microsoft.Extensions.Logging.ILoggerFactory,System.Text.Encodings.Web.UrlEncoder,Microsoft.Extensions.ObjectPool.ObjectPool{Microsoft.AspNetCore.Routing.Internal.UriBuildingContext},Microsoft.AspNetCore.Routing.IInlineConstraintResolver)</span><span class="sxs-lookup"><span data-stu-id="608e2-126">Microsoft.AspNetCore.Routing.Tree.TreeRouteBuilder(Microsoft.Extensions.Logging.ILoggerFactory,System.Text.Encodings.Web.UrlEncoder,Microsoft.Extensions.ObjectPool.ObjectPool{Microsoft.AspNetCore.Routing.Internal.UriBuildingContext},Microsoft.AspNetCore.Routing.IInlineConstraintResolver)</span></span>
- <span data-ttu-id="608e2-127">Microsoft.AspNetCore.Mvc.Formatters.OutputFormatterCanWriteContext</span><span class="sxs-lookup"><span data-stu-id="608e2-127">Microsoft.AspNetCore.Mvc.Formatters.OutputFormatterCanWriteContext</span></span>
- <span data-ttu-id="608e2-128">Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider)</span><span class="sxs-lookup"><span data-stu-id="608e2-128">Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider)</span></span>
- <span data-ttu-id="608e2-129">Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.Infrastructure.IActionActionResultTypeMapper)</span><span class="sxs-lookup"><span data-stu-id="608e2-129">Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.Infrastructure.IActionResultTypeMapper)</span></span>
- <span data-ttu-id="608e2-130">Microsoft.AspNetCore.Mvc.Formatters.FormatFilter(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})</span><span class="sxs-lookup"><span data-stu-id="608e2-130">Microsoft.AspNetCore.Mvc.Formatters.FormatFilter(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})</span></span>
- <span data-ttu-id="608e2-131">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ArrayModelBinder'1(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)</span><span class="sxs-lookup"><span data-stu-id="608e2-131">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ArrayModelBinder\`1(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)</span></span>
- <span data-ttu-id="608e2-132">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ByteArrayModelBinder</span><span class="sxs-lookup"><span data-stu-id="608e2-132">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ByteArrayModelBinder</span></span>
- [<span data-ttu-id="608e2-133">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.CollectionModelBinder'1(IModelBinder)</span><span class="sxs-lookup"><span data-stu-id="608e2-133">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.CollectionModelBinder\`1(IModelBinder)</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.modelbinding.binders.collectionmodelbinder-1.-ctor?view=aspnetcore-2.2#Microsoft_AspNetCore_Mvc_ModelBinding_Binders_CollectionModelBinder_1__ctor_Microsoft_AspNetCore_Mvc_ModelBinding_IModelBinder_)
- [<span data-ttu-id="608e2-134">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ComplexTypeModelBinder(IDictionary'2)</span><span class="sxs-lookup"><span data-stu-id="608e2-134">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ComplexTypeModelBinder(IDictionary\`2)</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.modelbinding.binders.complextypemodelbinder.-ctor?view=aspnetcore-2.2#Microsoft_AspNetCore_Mvc_ModelBinding_Binders_ComplexTypeModelBinder__ctor_System_Collections_Generic_IDictionary_Microsoft_AspNetCore_Mvc_ModelBinding_ModelMetadata_Microsoft_AspNetCore_Mvc_ModelBinding_IModelBinder__)
- <span data-ttu-id="608e2-135">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DictionaryModelBinder'2(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)</span><span class="sxs-lookup"><span data-stu-id="608e2-135">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DictionaryModelBinder\`2(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)</span></span>
- <span data-ttu-id="608e2-136">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DoubleModelBinder(System.Globalization.NumberStyles)</span><span class="sxs-lookup"><span data-stu-id="608e2-136">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DoubleModelBinder(System.Globalization.NumberStyles)</span></span>
- <span data-ttu-id="608e2-137">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FloatModelBinder(System.Globalization.NumberStyles)</span><span class="sxs-lookup"><span data-stu-id="608e2-137">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FloatModelBinder(System.Globalization.NumberStyles)</span></span>
- <span data-ttu-id="608e2-138">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormCollectionModelBinder</span><span class="sxs-lookup"><span data-stu-id="608e2-138">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormCollectionModelBinder</span></span>
- <span data-ttu-id="608e2-139">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormFileModelBinder</span><span class="sxs-lookup"><span data-stu-id="608e2-139">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormFileModelBinder</span></span>
- <span data-ttu-id="608e2-140">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.HeaderModelBinder</span><span class="sxs-lookup"><span data-stu-id="608e2-140">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.HeaderModelBinder</span></span>
- <span data-ttu-id="608e2-141">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.KeyValuePairModelBinder'2(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)</span><span class="sxs-lookup"><span data-stu-id="608e2-141">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.KeyValuePairModelBinder\`2(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)</span></span>
- <span data-ttu-id="608e2-142">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.SimpleTypeModelBinder(System.Type)</span><span class="sxs-lookup"><span data-stu-id="608e2-142">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.SimpleTypeModelBinder(System.Type)</span></span>
- <span data-ttu-id="608e2-143">Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes(System.Collections.Generic.IEnumerable{System.Object})</span><span class="sxs-lookup"><span data-stu-id="608e2-143">Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes(System.Collections.Generic.IEnumerable{System.Object})</span></span>
- <span data-ttu-id="608e2-144">Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes(System.Collections.Generic.IEnumerable{System.Object},System.Collections.Generic.IEnumerable{System.Object})</span><span class="sxs-lookup"><span data-stu-id="608e2-144">Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes(System.Collections.Generic.IEnumerable{System.Object},System.Collections.Generic.IEnumerable{System.Object})</span></span>
- <span data-ttu-id="608e2-145">Microsoft.AspNetCore.Mvc.ModelBinding.ModelBinderFactory(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})</span><span class="sxs-lookup"><span data-stu-id="608e2-145">Microsoft.AspNetCore.Mvc.ModelBinding.ModelBinderFactory(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})</span></span>
- <span data-ttu-id="608e2-146">Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinderFactory,Microsoft.AspNetCore.Mvc.ModelBinding.Validation.IObjectModelValidator)</span><span class="sxs-lookup"><span data-stu-id="608e2-146">Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinderFactory,Microsoft.AspNetCore.Mvc.ModelBinding.Validation.IObjectModelValidator)</span></span>
- [<span data-ttu-id="608e2-147">Microsoft.AspNetCore.Mvc.Routing.KnownRouteValueConstraint()</span><span class="sxs-lookup"><span data-stu-id="608e2-147">Microsoft.AspNetCore.Mvc.Routing.KnownRouteValueConstraint()</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.routing.knownroutevalueconstraint.-ctor?view=aspnetcore-2.2#Microsoft_AspNetCore_Mvc_Routing_KnownRouteValueConstraint__ctor)
- <span data-ttu-id="608e2-148">Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter</span><span class="sxs-lookup"><span data-stu-id="608e2-148">Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter</span></span>
- <span data-ttu-id="608e2-149">Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter(System.Boolean)</span><span class="sxs-lookup"><span data-stu-id="608e2-149">Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter(System.Boolean)</span></span>
- <span data-ttu-id="608e2-150">Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter(Microsoft.AspNetCore.Mvc.MvcOptions)</span><span class="sxs-lookup"><span data-stu-id="608e2-150">Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter(Microsoft.AspNetCore.Mvc.MvcOptions)</span></span>
- <span data-ttu-id="608e2-151">Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter</span><span class="sxs-lookup"><span data-stu-id="608e2-151">Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter</span></span>
- <span data-ttu-id="608e2-152">Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter(System.Boolean)</span><span class="sxs-lookup"><span data-stu-id="608e2-152">Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter(System.Boolean)</span></span>
- <span data-ttu-id="608e2-153">Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter(Microsoft.AspNetCore.Mvc.MvcOptions)</span><span class="sxs-lookup"><span data-stu-id="608e2-153">Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter(Microsoft.AspNetCore.Mvc.MvcOptions)</span></span>
- [<span data-ttu-id="608e2-154">Microsoft.AspNetCore.Mvc.TagHelpers.ImageTagHelper(IHostingEnvironment,IMemoryCache,HtmlEncoder,IUrlHelperFactory)</span><span class="sxs-lookup"><span data-stu-id="608e2-154">Microsoft.AspNetCore.Mvc.TagHelpers.ImageTagHelper(IHostingEnvironment,IMemoryCache,HtmlEncoder,IUrlHelperFactory)</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.taghelpers.imagetaghelper.-ctor?view=aspnetcore-2.2#Microsoft_AspNetCore_Mvc_TagHelpers_ImageTagHelper__ctor_Microsoft_AspNetCore_Hosting_IHostingEnvironment_Microsoft_Extensions_Caching_Memory_IMemoryCache_System_Text_Encodings_Web_HtmlEncoder_Microsoft_AspNetCore_Mvc_Routing_IUrlHelperFactory_)
- <span data-ttu-id="608e2-155">Microsoft.AspNetCore.Mvc.TagHelpers.LinkTagHelper(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelper)</span><span class="sxs-lookup"><span data-stu-id="608e2-155">Microsoft.AspNetCore.Mvc.TagHelpers.LinkTagHelper(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)</span></span>
- <span data-ttu-id="608e2-156">Microsoft.AspNetCore.Mvc.TagHelpers.ScriptTagHelper(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelper)</span><span class="sxs-lookup"><span data-stu-id="608e2-156">Microsoft.AspNetCore.Mvc.TagHelpers.ScriptTagHelper(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)</span></span>
- <span data-ttu-id="608e2-157">Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.RazorPageAdapter(Microsoft.AspNetCore.Mvc.Razor.RazorPage)</span><span class="sxs-lookup"><span data-stu-id="608e2-157">Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.RazorPageAdapter(Microsoft.AspNetCore.Mvc.Razor.RazorPageBase)</span></span>

<span data-ttu-id="608e2-158">**Vlastnosti**</span><span class="sxs-lookup"><span data-stu-id="608e2-158">**Properties**</span></span>

- <span data-ttu-id="608e2-159">Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieDomain</span><span class="sxs-lookup"><span data-stu-id="608e2-159">Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieDomain</span></span>
- <span data-ttu-id="608e2-160">Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieName</span><span class="sxs-lookup"><span data-stu-id="608e2-160">Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieName</span></span>
- <span data-ttu-id="608e2-161">Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookiePath</span><span class="sxs-lookup"><span data-stu-id="608e2-161">Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookiePath</span></span>
- <span data-ttu-id="608e2-162">Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.RequireSsl</span><span class="sxs-lookup"><span data-stu-id="608e2-162">Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.RequireSsl</span></span>
- <span data-ttu-id="608e2-163">Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.AllowInferringBindingSourceForCollectionTypesAsFromQuery</span><span class="sxs-lookup"><span data-stu-id="608e2-163">Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.AllowInferringBindingSourceForCollectionTypesAsFromQuery</span></span>
- <span data-ttu-id="608e2-164">Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.SuppressUseValidationProblemDetailsForInvalidModelStateResponses</span><span class="sxs-lookup"><span data-stu-id="608e2-164">Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.SuppressUseValidationProblemDetailsForInvalidModelStateResponses</span></span>
- <span data-ttu-id="608e2-165">Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.CookieName</span><span class="sxs-lookup"><span data-stu-id="608e2-165">Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.CookieName</span></span>
- <span data-ttu-id="608e2-166">Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Domain</span><span class="sxs-lookup"><span data-stu-id="608e2-166">Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Domain</span></span>
- <span data-ttu-id="608e2-167">Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Path</span><span class="sxs-lookup"><span data-stu-id="608e2-167">Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Path</span></span>
- <span data-ttu-id="608e2-168">Microsoft.AspNetCore.Mvc.DataAnnotations.MvcDataAnnotationsLocalizationOptions.AllowDataAnnotationsLocalizationForEnumDisplayAttributes</span><span class="sxs-lookup"><span data-stu-id="608e2-168">Microsoft.AspNetCore.Mvc.DataAnnotations.MvcDataAnnotationsLocalizationOptions.AllowDataAnnotationsLocalizationForEnumDisplayAttributes</span></span>
- <span data-ttu-id="608e2-169">Microsoft.AspNetCore.Mvc.Formatters.Xml.MvcXmlOptions.AllowRfc7807CompliantProblemDetailsFormat</span><span class="sxs-lookup"><span data-stu-id="608e2-169">Microsoft.AspNetCore.Mvc.Formatters.Xml.MvcXmlOptions.AllowRfc7807CompliantProblemDetailsFormat</span></span>
- <span data-ttu-id="608e2-170">Microsoft.AspNetCore.Mvc.MvcOptions.AllowBindingHeaderValuesToNonStringModelTypes</span><span class="sxs-lookup"><span data-stu-id="608e2-170">Microsoft.AspNetCore.Mvc.MvcOptions.AllowBindingHeaderValuesToNonStringModelTypes</span></span>
- <span data-ttu-id="608e2-171">Microsoft.AspNetCore.Mvc.MvcOptions.AllowKombinacefiltry authorizefilters</span><span class="sxs-lookup"><span data-stu-id="608e2-171">Microsoft.AspNetCore.Mvc.MvcOptions.AllowCombiningAuthorizeFilters</span></span>
- <span data-ttu-id="608e2-172">Microsoft.AspNetCore.Mvc.MvcOptions.AllowShortCircuitingValidationWhenNoValidatorsArePresent</span><span class="sxs-lookup"><span data-stu-id="608e2-172">Microsoft.AspNetCore.Mvc.MvcOptions.AllowShortCircuitingValidationWhenNoValidatorsArePresent</span></span>
- <span data-ttu-id="608e2-173">Microsoft.AspNetCore.Mvc.MvcOptions.AllowValidatingTopLevelNodes</span><span class="sxs-lookup"><span data-stu-id="608e2-173">Microsoft.AspNetCore.Mvc.MvcOptions.AllowValidatingTopLevelNodes</span></span>
- <span data-ttu-id="608e2-174">Zásady Microsoft.AspNetCore.Mvc.MvcOptions.InputFormatterExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="608e2-174">Microsoft.AspNetCore.Mvc.MvcOptions.InputFormatterExceptionPolicy</span></span>
- <span data-ttu-id="608e2-175">Microsoft.AspNetCore.Mvc.MvcOptions.SuppressBindingUndefinedValueToEnumType</span><span class="sxs-lookup"><span data-stu-id="608e2-175">Microsoft.AspNetCore.Mvc.MvcOptions.SuppressBindingUndefinedValueToEnumType</span></span>
- <span data-ttu-id="608e2-176">Microsoft.AspNetCore.Mvc.MvcViewOptions.AllowRenderingMaxLengthAttribute</span><span class="sxs-lookup"><span data-stu-id="608e2-176">Microsoft.AspNetCore.Mvc.MvcViewOptions.AllowRenderingMaxLengthAttribute</span></span>
- <span data-ttu-id="608e2-177">Microsoft.AspNetCore.Mvc.MvcViewOptions.SuppressTempDataAttributePrefix</span><span class="sxs-lookup"><span data-stu-id="608e2-177">Microsoft.AspNetCore.Mvc.MvcViewOptions.SuppressTempDataAttributePrefix</span></span>
- <span data-ttu-id="608e2-178">Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowAreas</span><span class="sxs-lookup"><span data-stu-id="608e2-178">Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowAreas</span></span>
- <span data-ttu-id="608e2-179">Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowDefaultHandlingForOptions</span><span class="sxs-lookup"><span data-stu-id="608e2-179">Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowDefaultHandlingForOptionsRequests</span></span>
- <span data-ttu-id="608e2-180">Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowMappingHeadRequestsToGetHandler</span><span class="sxs-lookup"><span data-stu-id="608e2-180">Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowMappingHeadRequestsToGetHandler</span></span>

<span data-ttu-id="608e2-181">**Metody**</span><span class="sxs-lookup"><span data-stu-id="608e2-181">**Methods**</span></span>

- <span data-ttu-id="608e2-182">Microsoft.AspNetCore.Mvc.LocalRedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)</span><span class="sxs-lookup"><span data-stu-id="608e2-182">Microsoft.AspNetCore.Mvc.LocalRedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)</span></span>
- <span data-ttu-id="608e2-183">Microsoft.AspNetCore.Mvc.RedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)</span><span class="sxs-lookup"><span data-stu-id="608e2-183">Microsoft.AspNetCore.Mvc.RedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)</span></span>
- <span data-ttu-id="608e2-184">Microsoft.AspNetCore.Mvc.RedirectToActionResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)</span><span class="sxs-lookup"><span data-stu-id="608e2-184">Microsoft.AspNetCore.Mvc.RedirectToActionResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)</span></span>
- <span data-ttu-id="608e2-185">Microsoft.AspNetCore.Mvc.RedirectToPageResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)</span><span class="sxs-lookup"><span data-stu-id="608e2-185">Microsoft.AspNetCore.Mvc.RedirectToPageResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)</span></span>
- <span data-ttu-id="608e2-186">Microsoft.AspNetCore.Mvc.RedirectToRouteResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)</span><span class="sxs-lookup"><span data-stu-id="608e2-186">Microsoft.AspNetCore.Mvc.RedirectToRouteResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)</span></span>
- <span data-ttu-id="608e2-187">Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(Microsoft.AspNetCore.Mvc.ActionContext,Microsoft.AspNetCore.Mvc.ModelBinding.IValueProvider,Microsoft.AspNetCore.Mvc.Abstractions.ParameterDescriptor)</span><span class="sxs-lookup"><span data-stu-id="608e2-187">Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(Microsoft.AspNetCore.Mvc.ActionContext,Microsoft.AspNetCore.Mvc.ModelBinding.IValueProvider,Microsoft.AspNetCore.Mvc.Abstractions.ParameterDescriptor)</span></span>
- [<span data-ttu-id="608e2-188">Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(ActionContext,IValueProvider,ParameterDescriptor,Object)</span><span class="sxs-lookup"><span data-stu-id="608e2-188">Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(ActionContext,IValueProvider,ParameterDescriptor,Object)</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.modelbinding.parameterbinder.bindmodelasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Mvc_ModelBinding_ParameterBinder_BindModelAsync_Microsoft_AspNetCore_Mvc_ActionContext_Microsoft_AspNetCore_Mvc_ModelBinding_IValueProvider_Microsoft_AspNetCore_Mvc_Abstractions_ParameterDescriptor_System_Object_)

<!--

#### Affected APIs

**Types**

- `T:Microsoft.AspNetCore.Diagnostics.Views.WelcomePage`
- `T:Microsoft.AspNetCore.DiagnosticsViewPage.Views.AttributeValue`
- `T:Microsoft.AspNetCore.DiagnosticsViewPage.Views.BaseView`
- `T:Microsoft.AspNetCore.DiagnosticsViewPage.Views.HelperResult`
- `T:Microsoft.AspNetCore.Mvc.Formatters.Xml.ProblemDetails21Wrapper`
- `T:Microsoft.AspNetCore.Mvc.Formatters.Xml.ValidationProblemDetails21Wrapper`
- `T:Microsoft.AspNetCore.Mvc.Razor.Compilation.ViewsFeatureProvider`
- `T:Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.PageArgumentBinder`
- `T:Microsoft.AspNetCore.Routing.IRouteValuesAddressMetadata`
- `T:Microsoft.AspNetCore.Routing.RouteValuesAddressMetadata`

**Constructors**

- `M:Microsoft.AspNetCore.Cors.Infrastructure.CorsService.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Cors.Infrastructure.CorsOptions})`
- `M:Microsoft.AspNetCore.Routing.Tree.TreeRouteBuilder.#ctor(Microsoft.Extensions.Logging.ILoggerFactory,System.Text.Encodings.Web.UrlEncoder,Microsoft.Extensions.ObjectPool.ObjectPool{Microsoft.AspNetCore.Routing.Internal.UriBuildingContext},Microsoft.AspNetCore.Routing.IInlineConstraintResolver)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.OutputFormatterCanWriteContext.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider)`
- `M:Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.Infrastructure.IActionResultTypeMapper)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.FormatFilter.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})",
"nameWithType": "FormatFilter.FormatFilter(IOptions<MvcOptions>)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ArrayModelBinder`1.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ByteArrayModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.CollectionModelBinder`1.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ComplexTypeModelBinder.#ctor(System.Collections.Generic.IDictionary{Microsoft.AspNetCore.Mvc.ModelBinding.ModelMetadata,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DictionaryModelBinder`2.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DoubleModelBinder.#ctor(System.Globalization.NumberStyles)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FloatModelBinder.#ctor(System.Globalization.NumberStyles)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormCollectionModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormFileModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.HeaderModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.KeyValuePairModelBinder`2.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.SimpleTypeModelBinder.#ctor(System.Type)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes.#ctor(System.Collections.Generic.IEnumerable{System.Object})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes.#ctor(System.Collections.Generic.IEnumerable{System.Object},System.Collections.Generic.IEnumerable{System.Object})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ModelBinderFactory.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinderFactory,Microsoft.AspNetCore.Mvc.ModelBinding.Validation.IObjectModelValidator)`
- `M:Microsoft.AspNetCore.Mvc.Routing.KnownRouteValueConstraint.#ctor`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.#ctor`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.#ctor(System.Boolean)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.#ctor(Microsoft.AspNetCore.Mvc.MvcOptions)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.#ctor`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.#ctor(System.Boolean)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.#ctor(Microsoft.AspNetCore.Mvc.MvcOptions)`
- `M:Microsoft.AspNetCore.Mvc.TagHelpers.ImageTagHelper.#ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)`
- `M:Microsoft.AspNetCore.Mvc.TagHelpers.LinkTagHelper.#ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)`
- `M:Microsoft.AspNetCore.Mvc.TagHelpers.ScriptTagHelper.#ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)`
- `M:Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.RazorPageAdapter.#ctor(Microsoft.AspNetCore.Mvc.Razor.RazorPageBase)`

**Properties**

- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieDomain`
- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieName`
- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookiePath`
- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.RequireSsl`
- `P:Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.AllowInferringBindingSourceForCollectionTypesAsFromQuery`
- `P:Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.SuppressUseValidationProblemDetailsForInvalidModelStateResponses`
- `P:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.CookieName`
- `P:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Domain`
- `P:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Path`
- `P:Microsoft.AspNetCore.Mvc.DataAnnotations.MvcDataAnnotationsLocalizationOptions.AllowDataAnnotationsLocalizationForEnumDisplayAttributes`
- `P:Microsoft.AspNetCore.Mvc.Formatters.Xml.MvcXmlOptions.AllowRfc7807CompliantProblemDetailsFormat`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowBindingHeaderValuesToNonStringModelTypes`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowCombiningAuthorizeFilters`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowShortCircuitingValidationWhenNoValidatorsArePresent`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowValidatingTopLevelNodes`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.InputFormatterExceptionPolicy`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.SuppressBindingUndefinedValueToEnumType`
- `P:Microsoft.AspNetCore.Mvc.MvcViewOptions.AllowRenderingMaxLengthAttribute`
- `P:Microsoft.AspNetCore.Mvc.MvcViewOptions.SuppressTempDataAttributePrefix`
- `P:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowAreas`
- `P:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowDefaultHandlingForOptionsRequests`
- `P:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowMappingHeadRequestsToGetHandler`

**Methods**

- `M:Microsoft.AspNetCore.Mvc.LocalRedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectToActionResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectToPageResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectToRouteResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(Microsoft.AspNetCore.Mvc.ActionContext,Microsoft.AspNetCore.Mvc.ModelBinding.IValueProvider,Microsoft.AspNetCore.Mvc.Abstractions.ParameterDescriptor)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(Microsoft.AspNetCore.Mvc.ActionContext,Microsoft.AspNetCore.Mvc.ModelBinding.IValueProvider,Microsoft.AspNetCore.Mvc.Abstractions.ParameterDescriptor,System.Object)`

-->
