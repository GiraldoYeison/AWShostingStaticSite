# AWShostingStaticSite
Hosting a Static Website
<h1>Hosting a Static Website in AWS</h1>
<div><b>Creation Date:</b> November 27, 2023</div>
<div><b>Created By:</b> Yeison Giraldo</div>

<div style="height: 24px">&#8203;</div>
<hr />
<div style="height: 24px">&#8203;</div>


<div><h2>💻 Static websites have unchanging content and lack backend processing capabilities</h2><p>They comprise HTML pages, images, style sheets, and all necessary files for website rendering. Unlike dynamic websites, static ones don't employ server-side scripting or a database. To introduce interactivity and execute programming logic on static webpages, JavaScript can be utilized, running directly in the user's web browser.</p><p></p><p>Hosting a static website on Amazon Simple Storage Service (Amazon S3) is a straightforward process. You can achieve this by uploading the content and configuring it for public access. The beauty of this approach lies in the absence of the need for servers. Amazon S3 provides a versatile solution for storing and retrieving any volume of data at any given time, accessible from anywhere on the web.</p><p></p><p>Upon completing the lab, you'll gain the ability to:</p><ol><li><p>Create a bucket in Amazon S3</p></li><li><p>Upload content to your bucket</p></li><li><p>Enable access to the objects within the bucket</p></li><li><p>Update the website</p></li></ol>
</div>

<div><h3>1. In the AWS Management Console, on the Services menu, choose S3.</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/6caaa472-32d6-482e-be19-e77a1af5a446/8c6e4094-4d76-4ccd-839c-2b9a0bed8a54.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=656&mark-y=343&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0yODQmaD03NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="In the AWS Management Console, on the Services menu, choose S3." />
</div>

<div><h3>2. Choose Create bucket</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/c8bf6b25-aca9-4a18-8cd3-00b47e825341/98e9b39d-6cf2-427a-a0c3-c40c7dab1e02.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=952&mark-y=372&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0yMTYmaD02MCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Choose Create bucket" />
</div>

<div><h3>3. Type "website-123"</h3>
<p>An S3 bucket name must be globally unique, and the naming space is shared among all AWS accounts. Once a bucket is created, its name becomes unavailable for use by any other AWS account in any AWS Region unless the bucket is deleted.</p><p></p><p>Therefore, for the purposes of this lab, it is recommended to employ a unique bucket name that incorporates a random number, for instance: "website-123."</p>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/59f09073-ebd8-4739-8b62-d394a6a8ff42/b93ea98f-2fd4-4751-a7a1-a5f40bb8e6eb.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=77&mark-y=366&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz04MjAmaD01NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Type &quot;website-123&quot;" />
</div>

<div><h3>4. Select ACLs enabled</h3>
<p>In the <strong>Object Ownership</strong> section, select <strong>ACLs enabled</strong>, then verify <strong>Bucket owner preferred</strong> is selected.</p>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/8c799853-3b52-4201-87a1-2cefa0f4a74e/5b375f79-f6a3-4c62-9778-d44893d3b201.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=667&mark-y=493&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0zMSZoPTMxJmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Select ACLs enabled" />
</div>

<div><h3>5. Uncheck Block all public access</h3>
<p>Clear <strong>Block all public access</strong>, then select the box that states <strong>I acknowledge that the current settings may result in this bucket and the objects within becoming public</strong>.</p>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/f2d66df8-ac71-4c4e-9212-03eb62610969/590cfc0c-ebfc-4cc9-ac4e-399361e997f3.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=82&mark-y=545&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0zMSZoPTMxJmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Uncheck Block all public access" />
</div>

<div><h3>6. Check I acknowledge that the current settings might result in this bucket and the objects within becoming public.</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/29ca0f7d-00d9-43e9-995a-39dae55909cc/0e11e083-c3bb-45de-b03a-41f39c4c159d.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=174&mark-y=775&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0zMSZoPTMxJmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Check I acknowledge that the current settings might result in this bucket and the objects within becoming public." />
</div>

<div><h3>7. Click on Create bucket</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/10019df2-b199-4374-ba4b-4409af576d32/51543b98-13c8-4446-9439-abd353f64476.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=993&mark-y=1121&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0yMDMmaD01MyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Create bucket" />
</div>

<div><h3>8. Click on website-3051</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/d921354c-155d-425a-92e4-1bce68170113/20b60f3b-09fa-442e-9ded-2ac4750858f7.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=121&mark-y=616&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xMDUmaD0yOSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on website-3051" />
</div>

<div><h3>9. Click on Properties</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/5318a2fa-bf0f-4d3d-9d5d-cf9f9628ddc8/45e35d5e-f65c-42d3-a0d2-874e2d10c42c.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=145&mark-y=142&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xMzMmaD03MCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Properties" />
</div>

<div><h3>10. Scroll to the Tags panel.</h3>
<p>Choose Edit then Add tag and enter:</p>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/b183e06d-500a-4c78-8e1d-ddca4249469e/92cb2023-8d32-47c4-a8d0-b7b2c4ab06ca.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=1060&mark-y=311&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz04NiZoPTQ1JmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Scroll to the Tags panel." />
</div>

<div><h3>11. Click on Add tag</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/a9f891ed-cc84-4012-bbac-7af5f2c656c4/5f09dabd-92c4-40e6-9bd9-07dc0b4df6f7.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=75&mark-y=388&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xNDYmaD01NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Add tag" />
</div>

<div><h3>12. Choose Edit then Add tag and enter:</h3>
<ul><li><p><strong>Key:</strong> <code>Department</code></p></li><li><p><strong>Value:</strong> <code>Marketing</code></p></li></ul>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/2a9489cf-7aab-45f5-82df-e5006ac6f467/18b85df7-57f8-4727-9cee-eb63cb6bb779.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=991&mark-y=541&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xOTkmaD01NiZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Choose Edit then Add tag and enter:" />
</div>

<div><h3>13. Stay in the Properties console.</h3>
<p>Scroll to the <strong>Static website hosting</strong> panel.</p>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/d97c2264-30cd-408e-934a-99ecd51d04f9/bb74526f-77ea-4809-9123-7f9f4dbba03b.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=1086&mark-y=739&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz04OCZoPTQ2JmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Stay in the Properties console." />
</div>

<div><h3>14. Configure the following settings:</h3>
<ul><li><p><strong>Static web hosting:</strong> Enable</p></li><li><p><strong>Hosting type:</strong> Host a static website</p></li><li><p><strong>Index document:</strong> <code>index.html</code></p><ul><li><p><strong>Note</strong>: You must enter this value, even though it is already displayed.</p></li></ul></li><li><p><strong>Error document:</strong> <code>error.html</code></p><p>Choose <strong>Save changes</strong></p></li></ul>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/e6f8ee9a-2764-44f8-9cd7-aaa26c8fea7b/70fdb8a3-7d97-4e10-bbb3-e371082c9e63.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=81&mark-y=963&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz04MTgmaD01NCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Configure the following settings:" />
</div>

<div><h3>15. In the Static website hosting panel, choose the link under Bucket website endpoint.</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/3f13d8d4-0374-4ee8-a34a-14b35b116965/3dc1debb-3422-46b1-af34-a6d8ec73ce7a.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.2768&fp-y=0.8900&fp-z=1.5609&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=199&mark-y=743&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkNGRjc0NDImdz02MzgmaD00MSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="In the Static website hosting panel, choose the link under Bucket website endpoint." />
</div>

<div><h3>16. Click on 403 Forbidden…</h3>
<p>You will receive a <em>403 Forbidden</em> message because the bucket permissions have not been configured yet. Keep this tab open in your web browser so that you can return to it later.</p><p>Your bucket has now been configured to host a static website.</p>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/95062660-92cf-4798-a975-ca53a00088a8/06c084ab-d5e9-4ffa-997e-40655daa51d9.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.1705&fp-z=1.0034&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=2&mark-y=153&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkNGRjc0NDImdz0xMTk2Jmg9MTAmZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on 403 Forbidden…" />
</div>

<div><h2># Task 2: Uploading content to your bucket</h2><p>In this task, you will upload the files that will serve as your static website to the bucket.</p>
</div>

<div><h3>17. Return to the Amazon S3 console and in the website-<123> bucket you created earlier, choose the Objects tab</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/9adc8fcc-9730-4485-a7f6-c331df428bf2/4fbe75c6-5427-45c8-a3a7-ffa00a1393f9.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=45&mark-y=195&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xMTAmaD03MCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Return to the Amazon S3 console and in the website-&lt;123&gt; bucket you created earlier, choose the Objects tab" />
</div>

<div><h3>18. Click on Upload</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/553e397d-bab5-45c3-a2ef-f0854ac97070/17725fd6-2cd9-4655-8c2c-3d33c780fb27.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=47&mark-y=375&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xMzQmaD00NSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Upload" />
</div>

<div><h3>19. Click on Add files</h3>
<p>Locate and select the three files that you downloaded.</p>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/8663946b-f135-424f-8c95-81afa9bdec37/073780e1-cc41-452d-ae52-28724c711a5c.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=840&mark-y=398&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xNTkmaD01OCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Add files" />
</div>

<div><h3>20. Click on Upload</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/00f250a6-ad32-4a22-b8a3-62a53276a35f/c02e741f-d7f3-4929-8dad-465dca3e8065.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=1047&mark-y=1085&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xNDImaD01OCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Upload" />
</div>

<div><h3>21. Click on Close</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/3d1df3b2-48f7-4e52-ac79-b1ff9c23baec/acbf57a7-34d1-40a2-b4ce-a267802487a2.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=1107&mark-y=100&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz05MyZoPTQxJmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Close" />
</div>

<div><h2># Task 3: Enabling access to the objects</h2><p>Objects that are stored in Amazon S3 are private by default. This ensures that your organization's data remains secure.</p><p>In this task, you will make the uploaded objects publicly accessible.</p>
</div>

<div><h2># You can make Amazon S3 objects public through two different ways:</h2><ul><li><p>To make either a whole bucket public, or a specific directory in a bucket public, use a <em>bucket policy</em>.</p></li><li><p>To make individual objects in a bucket public, use an <em>access control list (ACL)</em>.</p></li></ul><p>It is normally safer to make <em>individual objects</em> public because this avoids accidentally making other objects public. However, if you know that the entire bucket contains no sensitive information, you can use a <em>bucket policy</em>.</p><p>You will now configure the individual objects to be publicly accessible.</p>
</div>

<div><h3>22. Select all three objects.</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/6aced6ca-42c3-4f0c-b4f9-d3c240509fee/b793ed91-b978-4ea0-9685-1fecda56b79a.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=59&mark-y=520&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0yNSZoPTI1JmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Select all three objects." />
</div>

<div><h3>23. Click on Make public using ACL</h3>
<ol start="28"><li><p>In the <strong>Actions</strong> menu, choose <strong>Make public via ACL</strong>.</p><p>A list of the three objects is displayed.</p></li></ol>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/e3d0dd46-21ff-41e3-ab74-97a4b52f6e6e/400da208-8277-4a77-9381-21d474a9a7fd.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=811&mark-y=808&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0yNjkmaD00MSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Make public using ACL" />
</div>

<div><h3>24. Click on Make public</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/7b9358ba-c4b4-4922-b90d-f56c42af9030/7842db6e-8c34-47f8-9788-faa396a8a496.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=1002&mark-y=774&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xODgmaD01NCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Make public" />
</div>

<div><h3>25. Return to the web browser tab that has the 403 Forbidden message.</h3>
<p>Refresh the webpage.</p>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/62e805ff-16f4-4c23-b17a-5b8c2c42e3cc/c7df3914-f6a1-4e63-ae56-287b1b932fa6.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.4928&fp-y=0.8058&fp-z=1.0863&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=61&mark-y=594&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkNGRjc0NDImdz0xMDc4Jmg9MjY4JmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Return to the web browser tab that has the 403 Forbidden message." />
</div>

<div><h2># Task 4: Updating the website</h2><p>You can change the website by editing the HTML file and uploading it again to the S3 bucket.</p><p>Amazon S3 is an <em>object storage service</em>, so you must upload the whole file. This action replaces the existing object in your bucket. You cannot edit the contents of an object—instead, the whole object must be replaced.</p><p>Make changes to the original index.html and upload again</p>
</div>

<div><h3>26. Click on Upload</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/2430ceb2-bfdc-48a0-ad56-b62fbffc3891/4de5d256-cfb1-4f6e-bb12-c36b26d3d759.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=58&mark-y=385&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xMzImaD00NCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Upload" />
</div>

<div><h3>27. Click on Add files</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/96cc45ce-56b2-451e-be55-3b32bef90483/33287eee-22a6-498e-ac9b-779880b300c3.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=830&mark-y=395&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xNTcmaD01NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Add files" />
</div>

<div><h3>28. Select a file from upload menu</h3>
</div>

<div><h3>29. Click on Upload</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/08919944-0460-4a2d-9aca-f0629a01fd7a/3d6d9c9c-bb75-473d-9824-09e2c5f49a26.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=1050&mark-y=1111&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0xNDAmaD01NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Upload" />
</div>

<div><h3>30. Click on Make public using ACL</h3>
<p>Select <strong>index.html</strong> and use the <strong>Actions</strong> menu to choose the <strong>Make public via ACL</strong> option again.</p>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/fe4988ef-add1-41be-983c-e1a5d2efca5b/cc887150-3d78-478a-bc7c-cdc1dd6db7d2.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=814&mark-y=812&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz0yNzEmaD00MiZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Make public using ACL" />
</div>

<div><h3>31. Click on Make public</h3>
</div>

<div><h2><a href="http://website-3051.s3-website-us-east-1.amazonaws.com/"># My Static Website</a></h2></div>

<div><h3>32. Return to the web browser tab with the static website and refresh the page.</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/089bc846-acb7-466d-a7df-2315c3f903e3/7a36b8c4-5a76-4d4d-b782-1ad08c18cadb.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.4932&fp-y=0.7536&fp-z=1.2971&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=189&mark-y=556&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkNGRjc0NDImdz04MjImaD0xNDImZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Return to the web browser tab with the static website and refresh the page." />
</div>

<div><h3>33. Click on Buckets</h3>
<img src="https://images.tango.us/workflows/bfdb122a-9913-4c32-ab2b-161b3a4abef6/steps/d1c7216e-8d50-4cc2-bfb2-a0c1512787c4/870a584c-98b5-4ada-b888-ce92e20c2757.png?fm=png&crop=focalpoint&fit=crop&fp-x=0.5000&fp-y=0.5000&w=1200&border=2%2CF4F2F7&border-radius=8%2C8%2C8%2C8&border-radius-inner=8%2C8%2C8%2C8&blend-align=bottom&blend-mode=normal&blend-x=0&blend-w=1200&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n&mark-x=156&mark-y=19&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkNGRjc0NDImdz02NCZoPTMzJmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D" style="border-radius: 8px; border: 1px solid #F4F2F7;" width="600" alt="Click on Buckets" />
</div>

<div><h3>34. Congratulations, You're Done!</h3>
<p>Your static website is now reachable on the internet. Hosting it on Amazon S3 ensures high availability, allowing it to handle substantial traffic without the need for dedicated servers.</p><p></p><p>Additionally, you have the option to associate your custom domain name with the static website hosted on Amazon S3. This can be achieved by leveraging the Amazon Route 53 Domain Name System (DNS) service in conjunction with Amazon S3.</p>
</div>

<br/>
<hr/>
<div>

</div>
