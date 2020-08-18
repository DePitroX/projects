document.addEventListener('DOMContentLoaded', async function () {
const copyTextBtn = document.getElementById('copy-text-btn')
const copyImgBtn = document.getElementById('copy-img-btn')
const textarea = "to jest skopiuowany testk"
const canWriteEl = document.getElementById('can-write')
const errorEl = document.getElementById('errorMsg')
const img = document.querySelector('._87v3');

async function askWritePermission(){
	try{
		const{state}=await navigator.permissions.query({ name: 'clipboard-write', allowWithoutGesture: false })
		return state==='granted'
	}catch(x){
		errorEl.textContent=`Compatibility error (ONLY CHROME > V66): ${error.message}`
		console.log(x)
		return false
	}
}

const canWrite = await askWritePermission()

canWriteEl.textContent = canWrite
canWriteEl.style.color = canWrite ? 'green' : 'red'

copyImgBtn.disabled = copyTextBtn.disabled = !canWrite

const setToClipboard = blob => {
	const data = [new ClipboardItem({ [blob.type]: blob })]
	return navigator.clipboard.write(data)
}
document.addEventListener('click', async () => {console.log('klik1!');
	try{
		const response = await fetch(img.src)
		const blob = await response.blob()
		await setToClipboard(blob)
	}catch (x) {
		console.error('Something wrong happened')
		console.error(x)
	}
})

document.addEventListener('click', async () => {console.log('klik2!');
	try{
		const blob=new Blob([textarea], { type: 'text/plain' })
		await setToClipboard(blob)
	}catch(x){
		console.error('Something wrong happened:'+x)
	}
})
})
